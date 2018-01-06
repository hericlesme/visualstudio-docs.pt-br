---
title: "Conceitos básicos de integração de controle de origem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5d474e00186cf2110dd8e701d980a1a4562beb8c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-integration-essentials"></a>Conceitos básicos de integração de controle de origem
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]dá suporte a dois tipos de integração de controle de origem: um plug-in de controle de origem que fornece a funcionalidade básica e é criado usando a API de plug-in de controle de origem (anteriormente conhecida como a API MSSCCI) e uma solução de integração de controle de origem baseado em VSPackage que fornece a funcionalidade mais robusta.  
  
## <a name="source-control-plug-in"></a>Plug-in de controle de origem  
 Um plug-in de controle de origem é gravado como uma DLL que implementa a API de plug-in de controle de origem. Funcionalidade de integração de controle de origem e de registro é fornecida por meio da API. Essa abordagem é mais fácil de implementar do que um controle de origem VSPackage e usa o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface de usuário (UI) para a maioria das operações de controle de origem.  
  
 Para implementar um plug-in de usando a API de plug-in de controle de origem de controle de origem, siga estas etapas:  
  
1.  Criar uma DLL que implementa as funções especificadas na [Plug-ins de controle de origem](../../extensibility/source-control-plug-ins.md).  
  
2.  Registrar a DLL, tornando as entradas do registro apropriada, conforme descrito em [como: instalar um plug-in de controle de origem](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).  
  
3.  Criar um auxiliar de interface do usuário e exibi-lo quando solicitado pelo pacote de adaptador de controle de origem (o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componente que lida com a funcionalidade de controle de origem por meio de plug-ins de controle de origem).  
  
 Para obter mais informações, consulte [criar um plug-in de controle de origem](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## <a name="source-control-vspackage"></a>VSPackage de controle do código-fonte  
 Um controle de origem VSPackage implementação permite que você desenvolva uma substituição personalizada para o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] da interface do usuário do controle de origem. Essa abordagem fornece controle total sobre a integração de controle de origem, mas você deve fornecer os elementos de interface do usuário e implementar as interfaces de controle de origem caso contrário, pode ser fornecidas com a abordagem de plug-in.  
  
 Para implementar um VSPackage de controle do código-fonte, você deve:  
  
1.  Criar e registrar o seu próprio controle de origem VSPackage, conforme descrito em [registro e seleção](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
2.  Substitua o controle da fonte padrão da interface do usuário com a interface do usuário personalizada. Consulte [Interface de usuário personalizada](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3.  Especifique os glifos para ser usado e lidar com **Solution Explorer** eventos de glifo. Consulte [controle de glifo](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4.  Manipular eventos de consulta editar e salvar consulta, conforme mostrado no [consulta Editar consulta salvar](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).  
  
 Para obter mais informações, consulte [criar um VSPackage de controle do código-fonte](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral](../../extensibility/internals/source-control-integration-overview.md)   
 [Criando um controle de origem plug-in](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Criar um VSPackage de controle do código-fonte](../../extensibility/internals/creating-a-source-control-vspackage.md)