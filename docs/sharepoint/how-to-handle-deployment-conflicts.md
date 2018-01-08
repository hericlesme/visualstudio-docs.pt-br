---
title: "Como: resolver conflitos de implantação | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SharePoint development in Visual Studio, extending deployment
ms.assetid: 8e545873-3fed-46cf-a95f-27b5fc0d5f83
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: c908262a0ff74bb8574fd76f788611165934375b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-deployment-conflicts"></a>Como identificar conflitos de implantação
  Você pode fornecer seu próprio código para lidar com conflitos de implantação para um item de projeto do SharePoint. Por exemplo, você pode determinar se todos os arquivos no item de projeto atual já existem no local de implantação e, em seguida, exclua os arquivos de implantado antes que o item de projeto atual seja implantado. Para obter mais informações sobre conflitos de implantação, consulte [estendendo SharePoint empacotamento e implantação](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-handle-a-deployment-conflict"></a>Para lidar com um conflito de implantação  
  
1.  Crie uma extensão de item de projeto, uma extensão de projeto ou uma definição de um novo tipo de item de projeto. Para mais informações, consulte os seguintes tópicos:  
  
    -   [Como criar uma extensão de item do projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Como criar uma extensão de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Como definir um tipo de item do projeto do SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  Na extensão de lidar com o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> eventos de um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> objeto (em uma extensão de item de projeto ou a extensão de projeto) ou um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> objeto (em uma definição de um novo tipo de item de projeto).  
  
3.  No manipulador de eventos, determine se há um conflito entre o item de projeto que está sendo implantado e a solução implantada no site do SharePoint, com base em critérios que se aplicam ao seu cenário. Você pode usar o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> propriedade do parâmetro de argumentos de evento para analisar o item de projeto que está sendo implantado e você pode analisar os arquivos no local de implantação ao chamar um comando do SharePoint que você define para essa finalidade.  
  
     Para muitos tipos de conflitos, primeiro convém determinar qual etapa da implantação está em execução. Você pode fazer isso usando o <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> propriedade do parâmetro de argumentos de evento. Embora geralmente faz sentido para detectar conflitos durante o interno <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> etapa de implantação, você pode verificar conflitos durante qualquer etapa de implantação.  
  
4.  Se houver um conflito, use o <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> método o <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> propriedade dos argumentos do evento para criar um novo <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> objeto. Esse objeto representa o conflito de implantação. Em sua chamada para o <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> método, especifique também o método que é chamado para resolver o conflito.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra o processo básico para lidar com um conflito de implantação em uma extensão de item de projeto para itens de projeto de definição de lista. Para lidar com um conflito de implantação para um tipo diferente de item de projeto, passar uma cadeia de caracteres diferente para o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Para obter mais informações, consulte [estendendo itens de projeto do SharePoint](../sharepoint/extending-sharepoint-project-items.md).  
  
 Para simplificar, o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> manipulador de eventos neste exemplo presume que existe um conflito de implantação (ou seja, ele sempre adiciona um novo <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> objeto) e o `Resolve` método simplesmente retorna **true** para indicar que o conflito foi resolvido. Em um cenário real, o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> manipulador de eventos deve determinar primeiro se houver um conflito entre um arquivo no item de projeto atual e um arquivo no local de implantação e, em seguida, adicionar um <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> objeto apenas se houver um conflito. Por exemplo, você pode usar o `e.ProjectItem.Files` propriedade no manipulador de eventos para analisar os arquivos no item de projeto e você pode chamar um comando do SharePoint para analisar os arquivos no local de implantação. Da mesma forma, em um cenário real de `Resolve` método pode chamar um comando do SharePoint para resolver o conflito no site do SharePoint. Para obter mais informações sobre a criação de comandos do SharePoint, consulte [como: criar um comando SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer referências para os seguintes assemblies:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Implantando a extensão  
 Para implantar a extensão, criar um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacote de extensão (VSIX) para o assembly e outros arquivos que você quer distribuir com a extensão. Para obter mais informações, consulte [implantação de extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo empacotamento do SharePoint e implantação](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Estendendo itens de projeto do SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Como: executar código quando etapas de implantação são executadas](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Como criar um novo comando do SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)  
  
  