---
title: "Criar um VSPackage de controle do código-fonte | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4c3d414f1fcf6a7f4cd4155eb04e3696fb39740a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="creating-a-source-control-vspackage"></a>Criar um VSPackage de controle do código-fonte
Esta documentação inclui links para a visão geral da arquitetura de um pacote de controle do código-fonte integrado com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], a API que é definida por interfaces a serem implementadas e os serviços a serem consumidos e um exemplo que ilustra uma fonte simple controle a implementação do pacote.  
  
 Com um controle do código-fonte VSPackage, você pode criar um caminho de integração profunda para controle de origem integrar com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Ele permite que o pacote ignorar o controle de fonte padrão da interface do usuário hospedado pelo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], responder a solicitações de controle de origem do sistema de projeto e interagir com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componentes, tais como **Gerenciador de soluções**. O [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] capacita [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] parceiros com um mecanismo para criar um VSPackage que pode se integrar com [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usando um modelo de serviço.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Introdução](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Discute o pacote de controle de origem, que é uma alternativa mais avançada para o plug-in para implementar recursos de controle de origem no controle de origem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Arquitetura](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Apresenta um diagrama e explica os componentes de um pacote de controle de origem.  
  
 [Recursos](../../extensibility/internals/source-control-vspackage-features.md)  
 Descreve os vários recursos de um pacote de controle de origem.  
  
 [Elementos de design](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Descreve a estrutura do VSPackage que um pacote de controle de origem deve implementar para integração profunda.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Criar um plug-in de controle do código-fonte](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Discute como criar um plug-in de controle de origem que fornece funcionalidade de controle de origem no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface de usuário de controle de origem (UI).  
  
 [Controle do código-fonte](../../extensibility/internals/source-control.md)  
 Discute as opções para implementar o controle de origem como um recurso integrado do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].