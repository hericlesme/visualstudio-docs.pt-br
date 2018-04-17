---
title: 'Como: executar código quando um projeto SharePoint é implantado ou retraído | Microsoft Docs'
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
ms.openlocfilehash: c76d62751670e4fdd38c1ebb3042e5c403ee1ca6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Como executar código quando um projeto SharePoint é implantado ou retraído
  Se você quiser realizar tarefas adicionais quando um projeto do SharePoint é implantado ou recolhido, você pode manipular os eventos que são gerados pelo Visual Studio. Para obter mais informações, consulte [estendendo SharePoint empacotamento e implantação](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Para executar código quando um projeto do SharePoint é implantado ou cancelada  
  
1.  Crie uma extensão de item de projeto, uma extensão de projeto ou uma definição de um novo tipo de item de projeto. Para mais informações, consulte os seguintes tópicos:  
  
    -   [Como criar uma extensão de item do projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Como criar uma extensão de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Como definir um tipo de item do projeto do SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  Na extensão de acesso a <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objeto. Para obter mais informações, consulte [como: recuperar o serviço de projeto do SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
3.  Manipular o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> eventos do serviço de projeto.  
  
4.  No evento manipuladores, use o <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> para obter informações sobre a sessão atual de implantação. Por exemplo, você pode determinar qual projeto está na sessão atual de implantação e se ele está sendo implantado ou cancelada.  
  
 O exemplo de código a seguir demonstra como tratar o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> eventos em uma extensão de projeto. Essa extensão grava uma mensagem adicional para o **saída** janela quando a implantação é iniciado e concluído para um projeto do SharePoint.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer referências para os seguintes assemblies:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Implantando a extensão  
 Para implantar a extensão, criar um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacote de extensão (VSIX) para o assembly e outros arquivos que você quer distribuir com a extensão. Para obter mais informações, consulte [implantação de extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo empacotamento do SharePoint e implantação](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Como executar o código quando as etapas de implantação são executadas](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)  
  
  