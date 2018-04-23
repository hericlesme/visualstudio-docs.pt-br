---
title: Criar um VSPackage de controle do código-fonte | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8eb34efef22510d1d8f83590a6bdb7960d70ce49
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
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