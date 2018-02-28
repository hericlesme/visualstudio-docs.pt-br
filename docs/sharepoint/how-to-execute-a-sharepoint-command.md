---
title: 'Como: executar um comando do SharePoint | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], executing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 8cfbcf4b00e4551b568e9124e839423f58d922c9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-execute-a-sharepoint-command"></a>Como executar um comando SharePoint
  Se você quiser usar o modelo de objeto de servidor em uma extensão de ferramentas do SharePoint, você deve criar um personalizado *comando SharePoint* para chamar a API. Depois de definir o comando e implantá-lo com sua extensão de ferramentas do SharePoint, a sua extensão poderá executar o comando para chamar o modelo de objeto de servidor do SharePoint. Para executar o comando, use um dos métodos de ExecuteCommand um <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objeto.  
  
 Para obter mais informações sobre a finalidade de comandos do SharePoint, consulte [chamando os modelos de objeto do SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### <a name="to-execute-a-sharepoint-command"></a>Para executar um comando do SharePoint  
  
1.  Em sua extensão de ferramentas do SharePoint, obtenha um <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objeto. A maneira como você obtém uma <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objeto depende do tipo de extensão que você está criando:  
  
    -   Em uma extensão do sistema de projeto do SharePoint, use o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> propriedade.  
  
         Para obter mais informações sobre extensões de sistema do projeto, consulte [estendendo o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
    -   Em uma extensão do **conexões do SharePoint** nó **Server Explorer**, use o <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> propriedade. Para obter um <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> de objeto, use o <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> propriedade.  
  
         Para obter mais informações sobre **Server Explorer** extensões, consulte [estendendo o nó de conexões do SharePoint no Gerenciador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
    -   No código que não faz parte de uma extensão das ferramentas do SharePoint, como um Assistente de modelo de projeto, use o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> propriedade.  
  
         Para obter mais informações sobre como recuperar o serviço de projeto, consulte [usando o serviço de projeto do SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
2.  Chame um dos métodos de ExecuteCommand a <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objeto. Passe o nome do comando que você deseja executar para o primeiro argumento do método ExecuteCommand. Se o comando tiver um parâmetro personalizado, passe o parâmetro para o segundo argumento do método ExecuteCommand.  
  
     Há uma sobrecarga de ExecuteCommand diferente para cada assinatura de comando com suporte. A tabela a seguir lista as assinaturas com suporte e qual sobrecarregar a ser usado para cada assinatura.  
  
    |Assinatura de comando|Sobrecarga de ExecuteCommand usar|  
    |-----------------------|------------------------------------|  
    |O comando tem somente o padrão <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parâmetro e nenhum valor de retorno.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |O comando tem somente o padrão <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parâmetro e um valor de retorno.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |O comando tem dois parâmetros (o padrão <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parâmetro e um parâmetro personalizado) e nenhum valor de retorno.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |O comando tem dois parâmetros e um valor de retorno.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como usar o <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> sobrecarga para chamar o `Contoso.Commands.UpgradeSolution` comando descrito [como: criar um comando do SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]  
  
 O `Execute` método mostrado neste exemplo é uma implementação do <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> método o <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> interface em uma etapa de implantação personalizada. Para ver esse código no contexto de um exemplo maior, consulte [passo a passo: Criando uma etapa de implantação personalizada para projetos SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
 Observe os seguintes detalhes sobre a chamada para o <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> método:  
  
-   O primeiro parâmetro identifica o comando que você deseja chamar. Essa cadeia de caracteres corresponde ao valor que você passa para o <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> na definição de comando.  
  
-   O segundo parâmetro é o valor que você deseja passar para o segundo parâmetro personalizado do comando. Nesse caso, é o caminho completo do arquivo. wsp que está sendo atualizado para o site do SharePoint.  
  
-   O código não passa a implícita <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> ao comando. Este parâmetro é passado para o comando automaticamente quando você chama o comando de uma extensão do sistema de projeto do SharePoint ou uma extensão do **conexões do SharePoint** nó **Server Explorer**. Em outros tipos de soluções, como em um Assistente de modelo de projeto que implementa o <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interface, este parâmetro é **nulo**.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer uma referência ao assembly Microsoft.VisualStudio.SharePoint.  
  
## <a name="see-also"></a>Consulte também  
 [A chamada para os modelos de objeto do SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Como: criar um comando do SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Instruções passo a passo: estendendo o Gerenciador de Servidores para exibir Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  