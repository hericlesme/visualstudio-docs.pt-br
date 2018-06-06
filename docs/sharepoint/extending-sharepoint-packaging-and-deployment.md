---
title: Estendendo o SharePoint empacotamento e implantação | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 827024df92fe23799c4bbbe023bbf8e940dc507b
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767015"
---
# <a name="extend-sharepoint-packaging-and-deployment"></a>Estender o SharePoint empacotamento e implantação
  Você pode estender o empacotamento e o processo de implantação para projetos do SharePoint.
  
## <a name="create-deployment-steps"></a>Criar etapas de implantação
 Quando você implanta um projeto do SharePoint, [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] executa uma série de etapas de implantação. O Visual Studio inclui etapas de implantação interna para muitas tarefas, como o cancelamento e a adição de soluções. No entanto, você também pode criar suas próprias etapas de implantação.  
  
 Para uma explicação passo a passo que demonstre como criar uma etapa de implantação, consulte [passo a passo: Criando uma etapa de implantação personalizada para projetos SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## <a name="create-deployment-configurations"></a>Criar configurações de implantação
 Uma configuração de implantação é um conjunto de etapas de implantação que é executado para um determinado projeto, mas pode afetar todos os itens de projeto do SharePoint. Cada configuração de implantação inclui um conjunto de etapas que é executado quando o projeto é implantado e outro conjunto que é executado quando o projeto está recolhido. [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] inclui duas configurações de implantação interna, mas você também pode criar seus próprios. Quando você cria uma configuração de implantação, você pode incluir etapas de implantação interna e etapas de implantação que você criar.  
  
 Para uma explicação passo a passo que demonstre como criar uma configuração de implantação, consulte [passo a passo: Criando uma etapa de implantação personalizada para projetos SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>Executar o código quando uma solução do SharePoint é implantada ou cancelada
 Você pode manipular os eventos para executar tarefas adicionais quando uma solução do SharePoint é implantada ou cancelada. O Visual Studio gera eventos que você pode manipular nos seguintes cenários:  
  
-   Antes e depois da implantação de cada etapa é executada para um item de projeto do SharePoint. Para obter mais informações, consulte [como: executar código quando etapas de implantação são executadas](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).  
  
-   Antes e depois de um projeto do SharePoint é implantado ou cancelado. Para obter mais informações, consulte [como: executar código quando um projeto SharePoint é implantado ou retraído](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).  
  
## <a name="handle-deployment-conflicts"></a>Resolver conflitos de implantação
 Alguns tipos de itens de projeto do SharePoint, incluindo módulos, partes da Web, listar as instâncias e tipos de conteúdo, fornecem a resolução de conflitos internos de implantação. Quando você implanta uma solução que contém um desses itens de projeto, o Visual Studio primeiro verifica se um arquivo já existe no site do SharePoint com o mesmo nome, URL ou ID como um arquivo no item que você está implantando. Se houver um conflito, o Visual Studio automaticamente pode resolver o conflito, ou pode solicitar que você determine se você deseja que o Visual Studio resolver o conflito ou cancelar a implantação. Para obter mais informações, consulte [de solução de problemas do SharePoint empacotamento e implantação](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
 Você pode estender esse recurso, fornecendo seu próprio código que verifica e resolve conflitos de implantação. Para obter mais informações, consulte [como: manipular conflitos de implantação](../sharepoint/how-to-handle-deployment-conflicts.md).  
  
## <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>Executar operações de linha de comando antes ou depois de um projeto é implantado
 Se você quiser executar uma operação de linha de comando quando uma solução do SharePoint é implantada, você pode definir o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> propriedades de uma <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objeto. O Visual Studio executa esses comandos antes e depois que o projeto é implantado.  
  
 Em alguns casos, você pode ver os conflitos de implantação. Há várias maneiras diferentes para resolver conflitos. Para obter mais informações, consulte [de solução de problemas do SharePoint empacotamento e implantação](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
## <a name="customize-validation-rules"></a>Personalizar as regras de validação
 Antes de implantar um pacote de solução (. wsp), você pode criar a funcionalidade personalizada e o pacote de regras de validação para verificar se o recurso ou o pacote é válido. Por exemplo, você pode relatar erros, avisos ou informações aos desenvolvedores para ajudá-lo a corrigir problemas de validação. Para obter mais informações, consulte [como: Criar recurso de personalizada e regras de validação de pacote para soluções do SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
## <a name="see-also"></a>Consulte também
 [Como: executar código quando etapas de implantação são executadas](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Passo a passo: Criando uma etapa de implantação para projetos SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [Como: criar funcionalidade personalizada e regras de validação de pacote para soluções do SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)   
 [Estendendo o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  
