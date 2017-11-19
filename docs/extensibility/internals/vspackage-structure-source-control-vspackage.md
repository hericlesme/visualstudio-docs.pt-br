---
title: "Estrutura VSPackage (VSPackage de controle do código-fonte) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: "26"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4f8422e4333c1f1ccffc928ce9a43e4afa53cc7a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="vspackage-structure-source-control-vspackage"></a>Estrutura VSPackage (VSPackage de controle de origem)
O SDK do pacote de controle de origem fornece diretrizes para criar um VSPackage que permitem que um implementador de controle de origem para integrar a funcionalidade de controle de origem com o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente. Um VSPackage é um componente COM que normalmente é carregado sob demanda, o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE), de acordo com os serviços que estão sendo anunciados pelo pacote em suas entradas do registro. Cada VSPackage deve implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Um VSPackage geralmente consome serviços oferecidos pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE e proffers alguns serviços da sua própria.  
  
 Um VSPackage declara seus itens de menu e estabelece um estado de item padrão por meio do arquivo. VSCT. O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE exibe os itens de menu nesse estado até que o VSPackage é carregado. Subsequentemente, do VSPackage implementação de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método é chamado para habilitar ou desabilitar itens de menu.  
  
## <a name="source-control-package-characteristics"></a>Características do pacote de controle de origem  
 Um controle de origem VSPackage está profundamente integrado ao [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 A semântica de VSPackage incluem:  
  
-   Interface a ser implementada em virtude sendo um VSPackage (o `IVsPackage` interface)  
  
-   Implementação do comando de interface do usuário (arquivo. VSCT e a implementação do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface)  
  
-   Registro de VSPackage com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 O controle de origem VSPackage deve se comunicar com esses outros [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entidades:  
  
-   Projetos  
  
-   Editores  
  
-   Soluções  
  
-   Windows  
  
-   A tabela de documentos em execução  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Ambiente de serviços do Visual Studio que podem ser consumidos  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 Serviço SVsRegisterScciProvider  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>VSIP Interfaces implementadas e chamada  
 Um pacote de controle de origem é um VSPackage e, portanto, ele pode interagir diretamente com outros VSPackages registrados com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Para fornecer toda a funcionalidade de controle de origem, um controle de origem VSPackage pode lidar com interfaces fornecidas por projetos ou o shell.  
  
 Todos os projetos [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> seja reconhecido como um projeto dentro de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. No entanto, essa interface é especializada não suficiente para o controle de origem. Projetos que devem ser em fonte de controle de implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Essa interface é usada pelo controle de origem VSPackage para consultar um projeto para o seu conteúdo e fornecê-la glifos e informações de associação (as informações necessárias para estabelecer uma conexão entre o local do servidor e o local de disco de um projeto que está sob controle de origem).  
  
 O controle de origem VSPackage implementa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, que por sua vez permite que os projetos para se registrar para controle de origem e recuperar seus glifos de status.  
  
 Para obter uma lista completa de interfaces implementadas por um controle de origem VSPackage deve considerar, consulte [serviços relacionados e Interfaces](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## <a name="see-also"></a>Consulte também  
 [Elementos de design](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [Interfaces e serviços relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)