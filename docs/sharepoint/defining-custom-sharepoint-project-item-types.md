---
title: Definindo tipos de Item de projeto do SharePoint personalizado | Microsoft Docs
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
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 271cc2227e7bfca38f98a7424a18b314d01c92c6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="defining-custom-sharepoint-project-item-types"></a>Definindo tipos de item de projeto do SharePoint personalizados
  Defina um novo tipo de item de projeto do SharePoint quando você deseja criar um novo tipo de item de projeto do SharePoint. Por exemplo, o Visual Studio não inclui itens de projeto do SharePoint para adicionar campos ou ações personalizadas para um site do SharePoint. Você pode definir seus próprios tipos de itens de projeto do SharePoint para criar campos, ações personalizadas ou outros tipos de componentes do SharePoint.  
  
## <a name="tasks-for-defining-sharepoint-project-item-types"></a>Tarefas para definir tipos de Item de projeto do SharePoint  
 Para definir um tipo de item de projeto personalizado, crie um assembly de extensão do Visual Studio que implementa o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interface. Para obter mais informações, consulte [como: definir um tipo de Item de projeto do SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
 Quando você define um tipo de item de projeto personalizado, você também pode adicionar a seguinte funcionalidade para o item de projeto:  
  
-   Adicione um item de menu de atalho para o item de projeto. O item de menu é exibido quando você abrir o menu de atalho para o item de projeto no **Solution Explorer** chaves clicando com o item de projeto ou selecioná-la e, em seguida, escolhendo o Shift + F10. Para obter mais informações, consulte [como: adicionar um Item de Menu de atalho para um tipo de Item de projeto de SharePoint personalizados](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).  
  
-   Adicione uma propriedade personalizada para o item de projeto. A propriedade aparece no **propriedades** janela quando você escolhe o item de projeto no **Gerenciador de soluções**. Para obter mais informações, consulte [como: adicionar uma propriedade a um tipo de Item de projeto de SharePoint personalizados](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 Para habilitar outros desenvolvedores a usar o item de projeto no Visual Studio, crie um arquivo. spdata e criar um modelo de item ou um modelo de projeto que está associado ao item de projeto. Para obter mais informações, consulte [criando modelos de Item e modelos de projeto do SharePoint para itens de projeto](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## <a name="understanding-the-relationship-between-project-item-types-and-project-item-instances"></a>Noções básicas sobre a relação entre os tipos de Item de projeto e instâncias de Item de projeto  
 Quando você define um tipo de item de projeto do SharePoint, o Visual Studio carrega sua extensão quando um item de projeto do tipo associado é adicionado a um projeto do SharePoint. Por exemplo, se você definir uma nova **ação personalizada** tipo de item de projeto, o Visual Studio carrega sua extensão quando um usuário adiciona um **ação personalizada** item de projeto para um projeto. Visual Studio usa a mesma instância de sua extensão para todas as instâncias do tipo de item de projeto associado. No exemplo anterior, se o usuário adiciona um segundo **ação personalizada** item de projeto para o projeto, a mesma instância de sua extensão é usada para personalizar o segundo item de projeto.  
  
 Para acessar uma instância específica do seu tipo de item de projeto, lidar com uma da <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventos do *projectItemTypeDefinition* parâmetro em sua implementação do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> método. Por exemplo, para determinar quando um item de projeto de seu tipo personalizado é adicionado a um projeto, tratar o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> evento. Para obter mais informações, consulte [como: definir um tipo de Item de projeto do SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como: definir um tipo de Item de projeto do SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Como: adicionar uma propriedade a um tipo de Item de projeto do SharePoint personalizado](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Como: adicionar um Item de Menu de atalho para um tipo de Item de projeto do SharePoint personalizado](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Criando modelos de projeto e modelos de Item para itens de projeto do SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Passo a passo: Criando um Item de projeto de ação personalizada com um modelo de Item, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Passo a passo: Criando um Item de projeto da coluna de Site com um modelo de projeto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Passo a passo: Criando um Item de projeto de ação personalizada com um modelo de Item, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Passo a passo: Criando um Item de projeto da coluna de Site com um modelo de projeto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Implantando extensões para as Ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  