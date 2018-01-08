---
title: "Como: executar código quando etapas de implantação são executadas | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, extending deployment
ms.assetid: 6b0a52e5-e0ba-41bc-9e8a-1013e51fd3ba
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a147b9f6def49565334004bda1f8c4c80b0e7bfa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>Como executar código quando etapas de implantação são executadas
  Se você quiser executar tarefas adicionais para uma etapa de implantação em um projeto do SharePoint, você pode manipular os eventos que são gerados por itens de projeto do SharePoint antes e após cada etapa da implantação de execução do Visual Studio. Para obter mais informações, consulte [estendendo SharePoint empacotamento e implantação](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-run-code-when-deployment-steps-are-executed"></a>Para executar código quando etapas de implantação são executadas  
  
1.  Crie uma extensão de item de projeto, uma extensão de projeto ou uma definição de um novo tipo de item de projeto. Para mais informações, consulte os seguintes tópicos:  
  
    -   [Como criar uma extensão de item do projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Como criar uma extensão de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Como definir um tipo de item do projeto do SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  Na extensão de lidar com o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> eventos de um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> objeto (em uma extensão de item de projeto ou a extensão de projeto) ou um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> objeto (em uma definição de um novo tipo de item de projeto).  
  
3.  No evento manipuladores, use o <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> e <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> parâmetros para obter informações sobre a etapa da implantação. Por exemplo, você pode determinar qual etapa da implantação está em execução e se a solução está sendo implantado ou cancelada.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como tratar o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> eventos em uma extensão para o item de projeto de instância de lista. Essa extensão grava uma mensagem adicional para o **saída** janela quando o Visual Studio recicla o pool de aplicativos durante a implantação e o cancelamento da solução.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer referências para os seguintes assemblies:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Implantando a extensão  
 Para implantar a extensão, criar um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacote de extensão (VSIX) para o assembly e outros arquivos que você quer distribuir com a extensão. Para obter mais informações, consulte [implantação de extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo empacotamento do SharePoint e implantação](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Passo a passo: Criando uma etapa de implantação para projetos SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [Como executar o código quando um projeto do SharePoint é implantado ou retraído](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)  
  
  