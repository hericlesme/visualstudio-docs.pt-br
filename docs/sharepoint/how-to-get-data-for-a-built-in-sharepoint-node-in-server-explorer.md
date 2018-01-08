---
title: "Como: obter dados para um nó SharePoint interno no Gerenciador de servidores | Microsoft Docs"
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
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
ms.assetid: 86d04e0a-c114-427e-9945-da5fa339fda4
caps.latest.revision: "7"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: fa518bf566671dda2b54489fa37460840365bc70
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>Como obter dados para um nó SharePoint interno no Gerenciador de Servidores
  Para cada nó SharePoint interno no **Server Explorer**, você pode obter dados para o componente do SharePoint subjacente que representa o nó. Para obter mais informações, consulte [estendendo o nó de conexões do SharePoint no Gerenciador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como obter dados para a lista do SharePoint subjacente que representa uma lista de nós em **Server Explorer**. Por padrão, nós da lista têm um **exibir no navegador** item de menu de contexto que você pode clicar para abrir a lista em um navegador da Web. Este exemplo estende a nós da lista, adicionando um **exibição no Visual Studio** item de menu de contexto que abre as listas diretamente no Visual Studio. O código que acessa os dados de lista para o nó obter a URL da lista para abrir no Visual Studio.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]  
  
 Este exemplo usa o serviço de projeto do SharePoint para obter o <xref:EnvDTE.DTE> objeto que é usado para abrir lista no Visual Studio. Para obter mais informações sobre o serviço de projeto do SharePoint, consulte [usando o serviço de projeto do SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
 Para obter mais informações sobre as tarefas básicas para criar uma extensão para um nó SharePoint, consulte [como: estender um nó SharePoint no Gerenciador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer referências para os seguintes assemblies:  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Implantando a extensão  
 Para implantar o **Server Explorer** extensão, criar um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacote de extensão (VSIX) para o assembly e outros arquivos que você quer distribuir com a extensão. Para obter mais informações, consulte [implantação de extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo o nó de conexões do SharePoint no Gerenciador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Como: estender um nó SharePoint no Gerenciador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Usando o serviço de projeto do SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Implantando extensões para as Ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  