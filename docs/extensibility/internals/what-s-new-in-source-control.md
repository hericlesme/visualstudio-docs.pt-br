---
title: O que&#39;novo no controle do código-fonte | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b46730ab1acac6605af2e1ff1c418dbe8c886406
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31137762"
---
# <a name="what39s-new-in-source-control"></a>O que&#39;novo no controle de origem
Em [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] você pode fornecer uma solução de controle de origem profundamente integrado ao implementar um controle de origem VSPackage. Esta seção descreve os recursos de controle de origem VSPackages e fornece uma visão geral das etapas de implementação.  
  
## <a name="the-source-control-vspackage"></a>O VSPackage de controle do código-fonte  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oferece suporte a dois tipos de soluções de controle de origem. Todas as versões do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], você ainda pode integrar uma API de plug-in de controle de origem com base em plug-in. Você também pode criar um VSPackage para controle de origem que fornece uma integração profunda [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] caminho adequado para soluções de controle de origem que exigem um alto nível de sofisticação e autonomia.  
  
 Um VSPackage pode adicionar a praticamente qualquer tipo de funcionalidade para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Um controle de origem VSPackage fornece um recurso de controle do código-fonte completo para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], da interface do usuário apresentada ao usuário para a comunicação de back-end com o sistema de controle de origem.  
  
 Implementação de um controle de origem VSPackage requer uma estratégia "tudo ou nada". O criador de um controle de origem VSPackage deve investir uma quantidade significativa de esforço na implementação de um número de interfaces de controle de origem e novos elementos de interface do usuário (caixas de diálogo, menus e barras de ferramentas) para cobrir a funcionalidade de controle de origem inteiro, bem como interfaces necessário de qualquer pacote para integrar com êxito com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 As etapas a seguir oferecem uma visão geral sobre o que é necessário para implementar um pacote de controle de origem. Para obter detalhes, consulte [criar um VSPackage de controle do código-fonte](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1.  Crie um VSPackage que proffers um serviço de controle de origem particular.  
  
2.  Implementar as interfaces nos serviços relacionados ao controle de origem que são dedicaram por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (por exemplo, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> interface).  
  
3.  Registre o controle de origem VSPackage.  
  
4.  Implemente todo o controle de origem da interface do usuário, incluindo itens de menu, caixas de diálogo, barras de ferramentas e menus de contexto.  
  
5.  Todos os eventos relacionados ao controle de origem são passados para o controle de origem VSackage quando ele estiver ativo e deve ser tratado pelo seu VSPackage.  
  
6.  O controle de origem VSPackage deve escutar eventos, como aqueles Implementando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> interface, bem como eventos de documento de projeto de controle (TPD) (conforme implementado pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interface) e tomar as medidas necessárias.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Visão geral](../../extensibility/internals/source-control-integration-overview.md)   
 [Criar um VSPackage de controle do código-fonte](../../extensibility/internals/creating-a-source-control-vspackage.md)