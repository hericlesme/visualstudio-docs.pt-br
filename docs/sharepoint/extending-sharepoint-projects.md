---
title: Estendendo projetos SharePoint | Microsoft Docs
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
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 403ff3793dfd5ae4211444868af8c37dbd908672
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="extending-sharepoint-projects"></a>Estendendo projetos SharePoint
  Crie uma extensão de projeto quando você desejar personalizar os recursos de nível de projeto de projetos do SharePoint. Por exemplo, você pode adicionar propriedades de projeto personalizados ou responder a eventos de nível de projeto que são gerados quando o usuário desenvolve uma solução do SharePoint no Visual Studio.  
  
## <a name="creating-project-extensions"></a>Criando extensões de projeto  
 Para estender um item de projeto, criar um assembly de extensão do Visual Studio que implementa o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interface. Para obter mais informações, consulte [como: criar uma extensão de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
 Quando você cria uma extensão de projeto, você também pode adicionar a seguinte funcionalidade para os projetos do SharePoint:  
  
-   Adicione um item de menu de atalho. O item de menu é exibido quando você abrir o menu de atalho para um nó de projeto do SharePoint no **Solution Explorer** clicando duas vezes no nó ou selecioná-la e, em seguida, escolha a tecla Shift + F10 chaves. Para obter mais informações, consulte [como: adicionar um Item de Menu de atalho a projetos do SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).  
  
-   Adicione uma propriedade personalizada. A propriedade aparece no **propriedades** janela quando você escolhe um projeto do SharePoint no **Gerenciador de soluções**. Para obter mais informações, consulte [como: adicionar uma propriedade a projetos SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 Para uma explicação passo a passo que demonstre como criar, implantar e testar uma extensão de projeto, consulte [passo a passo: Criando uma extensão de projeto do SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).  
  
## <a name="understanding-the-relationship-between-project-extensions-and-project-instances"></a>Noções básicas sobre a relação entre as extensões de projeto e instâncias de projeto  
 Quando você cria uma extensão de projeto, a extensão carrega quando qualquer tipo de projeto do SharePoint é aberto em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]inclui vários modelos de projeto do SharePoint como definições de lista, tipos de conteúdo e receptores de evento. No entanto, há apenas um tipo de projeto do SharePoint. Os tipos de projeto que aparecem no **novo projeto** caixa de diálogo são apenas os modelos que juntos agrupar um ou mais itens de projeto do SharePoint. Como há apenas um tipo de projeto do SharePoint, as extensões criadas para um projeto se aplicam a todos os projetos do SharePoint. Por exemplo, você não pode criar uma extensão que se aplica apenas a um **tipo de conteúdo** projeto.  
  
 Para acessar uma instância específica do projeto, lidar com uma da <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> eventos do *projectService* parâmetro em sua implementação do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> método. Por exemplo, para determinar quando um projeto do SharePoint é adicionado a uma solução, tratar o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> evento. Para obter mais informações, consulte [como: criar uma extensão de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar uma extensão de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Como: adicionar um Item de Menu de atalho a projetos do SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Como: adicionar uma propriedade a projetos do SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Passo a passo: Criando uma extensão de projeto do SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [Definindo tipos de Item de projeto do SharePoint personalizado](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Estendendo itens de projeto do SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Estendendo empacotamento do SharePoint e implantação](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Estendendo o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  