---
title: Estendendo itens de projeto do SharePoint | Microsoft Docs
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
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
ms.assetid: f09f6664-196d-46d6-819f-3c6500f23536
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ffbacd5748ae2a5284ed628dce974b20e25bcab3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="extending-sharepoint-project-items"></a>Estendendo itens de projeto do SharePoint
  Crie uma extensão de item de projeto quando você deseja adicionar funcionalidade a um tipo de item de projeto do SharePoint que já está instalado no Visual Studio. Por exemplo, você pode criar uma extensão para o interno **receptor de evento** ou **definição de lista** itens de projeto no Visual Studio, ou você pode criar uma extensão para um tipo de item de projeto personalizados. Você também pode criar uma extensão para todos os tipos de itens de projeto do SharePoint.  
  
## <a name="tasks-for-extending-sharepoint-project-items"></a>Tarefas para estender os itens de projeto do SharePoint  
 Para estender um item de projeto, criar um assembly de extensão do Visual Studio que implementa o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interface. Para obter mais informações, consulte [como: criar uma extensão de Item de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
 Quando você estende um item de projeto, você também pode adicionar a seguinte funcionalidade para o item de projeto:  
  
-   Adicione um item de menu de atalho para o item de projeto. O item de menu é exibido quando você abrir o menu de atalho para o item de projeto no **Gerenciador de soluções**. Abra o menu de atalho clicando com o item de projeto ou selecioná-la e, em seguida, escolhendo o Shift + F10 chaves. Para obter mais informações, consulte [como: adicionar um Item de Menu de atalho para uma extensão de Item de projeto do SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).  
  
-   Adicione uma propriedade personalizada para o item de projeto. A propriedade aparece no **propriedades** janela quando você escolhe o item de projeto no **Gerenciador de soluções**. Para obter mais informações, consulte [como: adicionar uma propriedade a uma extensão de Item de projeto do SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).  
  
 Para uma explicação passo a passo que demonstre como criar, implantar e testar uma extensão de item de projeto, consulte [passo a passo: estendendo um tipo de Item de projeto do SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).  
  
## <a name="understanding-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Noções básicas sobre a relação entre as extensões de Item de projeto e instâncias de Item de projeto  
 Quando você cria uma extensão de item de projeto, o Visual Studio carrega sua extensão quando um item de projeto do tipo associado é adicionado a um projeto do SharePoint. Por exemplo, se você criar uma extensão para **receptor de evento** itens de projeto, o Visual Studio carrega sua extensão quando um usuário adiciona um **receptor de evento** item de projeto para um projeto. Visual Studio usa a mesma instância de sua extensão para todas as instâncias do tipo de item de projeto associado. No exemplo anterior, se o usuário adiciona um segundo **receptor de evento** item de projeto para o projeto, a mesma instância de sua extensão é usada para personalizar o segundo item de projeto.  
  
 Para acessar uma instância específica do tipo de item de projeto estiver estendendo, lidar com uma da <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventos do *projectItemType* parâmetro em sua implementação do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> método. Por exemplo, para determinar quando um item de projeto do tipo que você estiver estendendo é adicionado a um projeto, tratar o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> evento. Para obter mais informações, consulte [como: criar uma extensão de Item de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
## <a name="identifiers-for-sharepoint-project-items"></a>Identificadores para itens de projeto do SharePoint  
 Cada item de projeto do SharePoint tem um identificador de cadeia de caracteres correspondente. Você deve saber o identificador para um item de projeto para executar as seguintes tarefas:  
  
-   Crie uma extensão para o item de projeto. Nesse caso, você deve passar o identificador do item de projeto que você deseja estender para o construtor do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Para criar uma extensão para todos os tipos de projeto item, passe o  **\***  valor de cadeia de caracteres.  
  
-   Adicione o item de projeto para um projeto por meio de programação. Nesse caso, você deve passar o identificador do item de projeto para o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> método.  
  
 A tabela a seguir lista os identificadores para os itens de projeto do SharePoint que estão incluídos com o Visual Studio.  
  
|Nome do item de projeto|Identificador de cadeia de caracteres|  
|-----------------------|-----------------------|  
|Modelo de catálogo de dados corporativos|Microsoft.VisualStudio.SharePoint.BusinessDataConnectivity|  
|Tipo de Conteúdo|Microsoft.VisualStudio.SharePoint.ContentType|  
|Receptor de evento|Microsoft.VisualStudio.SharePoint.EventHandler|  
|Elemento vazio|Microsoft.VisualStudio.SharePoint.GenericElement|  
|Definição de lista<br /><br /> Definição de lista do tipo de conteúdo|Microsoft.VisualStudio.SharePoint.ListDefinition|  
|Instância de lista|Microsoft.VisualStudio.SharePoint.ListInstance|  
|Módulo|Microsoft.VisualStudio.SharePoint.Module|  
|Fluxo de trabalho sequencial<br /><br /> Fluxo de trabalho de máquina de estado|Microsoft.VisualStudio.SharePoint.Workflow|  
|Definição de site|Microsoft.VisualStudio.SharePoint.SiteDefinition|  
|Web Part Visual|Microsoft.VisualStudio.SharePoint.VisualWebPart|  
|Web Part|Microsoft.VisualStudio.SharePoint.WebPart|  
|Formulário de associação de fluxo de trabalho|Microsoft.VisualStudio.SharePoint.WorkflowAssociation|  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar uma extensão de Item de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Como: adicionar um Item de Menu de atalho para uma extensão de Item de projeto do SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Como: adicionar uma propriedade a uma extensão de Item de projeto do SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Passo a passo: Estendendo um tipo de Item de projeto do SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)   
 [Estendendo o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  