---
title: 'Como: adicionar um Item de Menu de atalho para um tipo de Item de projeto do SharePoint personalizado | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1fa954c2f24daa17ce4f1ed9aeb90df9f4566e58
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Como adicionar um item de menu de atalho a um item de projeto do SharePoint personalizado
  Quando você define um tipo de item de projeto do SharePoint personalizado, você pode adicionar um item de menu de atalho para o item de projeto. O item de menu é exibido quando um usuário clica o item de projeto no **Gerenciador de soluções**.  
  
 As etapas a seguir pressupõem que você já definiu seu próprio tipo de item de projeto do SharePoint. Para obter mais informações, consulte [como: definir um tipo de Item de projeto do SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>Para adicionar um item de menu de atalho para um tipo de item de projeto personalizados  
  
1.  No <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> método de seu <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementação, o identificador de <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> eventos do *projectItemTypeDefinition* parâmetro.  
  
2.  No seu manipulador de eventos para o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> evento, adicione um novo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> do objeto para o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> ou <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> coleção de parâmetro dos argumentos do evento.  
  
3.  No <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> manipulador de eventos para o novo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> do objeto, execute as tarefas que você deseja executar quando um usuário escolhe o item de menu de atalho.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como adicionar um item de menu de contexto para um tipo de item de projeto personalizados. Quando o usuário abre o menu de atalho do item de projeto **Solution Explorer** e escolhe o **mensagem de gravação para a janela de saída** item de menu, o Visual Studio exibe uma mensagem no **saída**  janela.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb#4)]  
  
 Este exemplo usa o serviço de projeto do SharePoint para gravar a mensagem para o **saída** janela. Para obter mais informações, consulte [usando o serviço de projeto do SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer um projeto de biblioteca de classes com as referências para os seguintes assemblies:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-project-item"></a>Implantando o Item de projeto  
 Para habilitar outros desenvolvedores a usar o item de projeto, crie um modelo de projeto ou um modelo de item de projeto. Para obter mais informações, consulte [criando modelos de Item e modelos de projeto do SharePoint para itens de projeto](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Para implantar o item de projeto, criar um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacote de extensão (VSIX) para o assembly, o modelo e outros arquivos que você quer distribuir com o item de projeto. Para obter mais informações, consulte [implantação de extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como: definir um tipo de Item de projeto do SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Como: adicionar uma propriedade a um tipo de Item de projeto do SharePoint personalizado](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Definindo tipos de item de projeto personalizados do SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  