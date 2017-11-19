---
title: 'Como: adicionar um Item de Menu de atalho a projetos do SharePoint | Microsoft Docs'
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
ms.assetid: bb251fe9-f1bf-4ddd-9359-4b7f78fbd50f
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0e327a716fc77dbc8dd3515c092dcd32c2da5158
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Como adicionar um item de menu de atalho a projetos do SharePoint
  Você pode adicionar um item de menu de atalho para qualquer projeto do SharePoint. O item de menu é exibido quando um usuário clica em um nó do projeto **Gerenciador de soluções**.  
  
 As etapas a seguir pressupõem que você já tenha criado uma extensão de projeto. Para obter mais informações, consulte [como: criar uma extensão de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-shortcut-menu-item-to-sharepoint-projects"></a>Para adicionar um item de menu de atalho a projetos do SharePoint  
  
1.  No <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> método de seu <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementação, o identificador de <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> eventos do *projectService* parâmetro.  
  
2.  No seu manipulador de eventos para o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> evento, adicione um novo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> do objeto para o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> ou <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> coleção de parâmetro dos argumentos do evento.  
  
3.  No <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> manipulador de eventos para o novo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> do objeto, execute as tarefas que você deseja executar quando um usuário clica o item de menu de atalho.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como adicionar um item de menu de atalho para nós de projeto do SharePoint no **Gerenciador de soluções**. Quando o usuário clica um nó do projeto e clica o **mensagem de gravação para a janela de saída** item de menu, o Visual Studio exibe uma mensagem no **saída** janela. Este exemplo usa o serviço de projeto do SharePoint para exibir a mensagem. Para obter mais informações, consulte [usando o serviço de projeto do SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/CSharp/projectmenu/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../sharepoint/codesnippet/VisualBasic/projectmenu/extension/projectitemextensionmenu.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer um projeto de biblioteca de classes com as referências para os seguintes assemblies:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Implantando a extensão  
 Para implantar a extensão, criar um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacote de extensão (VSIX) para o assembly e outros arquivos que você quer distribuir com a extensão. Para obter mais informações, consulte [implantação de extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo projetos SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Como: criar uma extensão de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [Como adicionar uma propriedade a projetos do SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)  
  
  