---
title: "Associando dados personalizados com o SharePoint extensões de ferramentas | Microsoft Docs"
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
- projects [SharePoint development in Visual Studio], associating custom data
- project items [SharePoint development in Visual Studio], associating custom data
- SharePoint project items, associating custom data
- SharePoint projects, associating custom data
- SharePoint development in Visual Studio, extensibility features
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8868300375d34664ba267b473f24d2c6a91ddd55
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="associating-custom-data-with-sharepoint-tools-extensions"></a>Associando dados personalizados a extensões de ferramentas do SharePoint
  Você pode adicionar dados personalizados a certos objetos em extensões de ferramentas do SharePoint. Isso é útil quando você tiver dados em uma parte de sua extensão que você deseja acessar posterior do código em sua extensão. Em vez de implementar uma maneira personalizada para armazenar e acessar dados, você pode associar os dados um objeto em sua extensão e, em seguida, recuperar os dados do mesmo objeto mais tarde.  
  
 Adicionando dados personalizados a objetos também é útil quando você quiser preservar os dados que são relevantes para um item específico no Visual Studio. Extensões de ferramentas do SharePoint são carregadas apenas uma vez no Visual Studio, para sua extensão pode trabalhar com vários itens diferentes (como projetos, itens de projeto ou **Server Explorer** nós) a qualquer momento. Se você tiver dados personalizados que são relevantes apenas para um item específico, você pode adicionar os dados para o objeto que representa o item.  
  
 Quando você adicionar dados personalizados a objetos em extensões de ferramentas do SharePoint, os dados não persistirão. Os dados estão disponíveis somente durante o tempo de vida do objeto. Depois que o objeto é recuperado pela coleta de lixo, os dados serão perdidos.  
  
 Extensões do sistema de projeto do SharePoint, você também pode salvar os dados de cadeia de caracteres que persiste depois que uma extensão é descarregada. Para obter mais informações, consulte [salvando dados em extensões do sistema de projeto do SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="objects-that-can-contain-custom-data"></a>Objetos que podem conter dados personalizados  
 Você pode adicionar dados personalizados para qualquer objeto no modelo de objeto do SharePoint ferramentas que implementa o <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interface. Essa interface define apenas uma propriedade, <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>, que é uma coleção de objetos de dados personalizado. Os seguintes tipos de implementam <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>  
  
## <a name="adding-and-retrieving-custom-data"></a>Adicionar e recuperar dados personalizados  
 Para adicionar dados personalizados a um objeto em uma extensão de ferramentas do SharePoint, obtenha o <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriedade do objeto que você deseja adicionar os dados e, em seguida, usar o <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> para adicionar os dados ao objeto.  
  
 Para recuperar dados personalizados de um objeto em uma extensão de ferramentas do SharePoint, obtenha o <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriedade do objeto e, em seguida, use um dos seguintes métodos:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>. Este método retorna **true** se o objeto de dados existir, ou **false** se ele não existe. Você pode usar esse método para recuperar instâncias dos tipos de valor ou tipos de referência.  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>. Esse método retorna os dados de objeto se ele existir, ou **nulo** se ele não existe. Você pode usar esse método somente para recuperar instâncias dos tipos de referência.  
  
 O exemplo de código a seguir determina se um determinado objeto de dados já está associado um item de projeto. Se o objeto de dados já não está associado ao item de projeto, o código adiciona o objeto para o <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriedade do item de projeto. Para ver esse exemplo no contexto de um exemplo maior, consulte [como: adicionar uma propriedade a um tipo de Item de projeto de SharePoint personalizados](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#13)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#13)]  
  
## <a name="see-also"></a>Consulte também  
 [Conceitos de programação e recursos para extensões de ferramentas do SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Passo a passo: Criando um Item de projeto de ação personalizada com um modelo de Item, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Passo a passo: Estendendo o Gerenciador de servidores para exibir Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Como: adicionar uma propriedade a projetos do SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Como: adicionar uma propriedade a um tipo de Item de projeto do SharePoint personalizado] (.. /SharePoint/How-to-Add-a-property-to-a-Custom-SharePoint-Project-Item-Type.MD   
  