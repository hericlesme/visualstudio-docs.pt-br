---
title: 'Como: definir um tipo de Item de projeto do SharePoint | Microsoft Docs'
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
ms.assetid: 18b56e7c-4efb-47a2-abfc-e9018ae38267
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: fb19c360f19890c7e9c116ad721dd99ef633d47a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-sharepoint-project-item-type"></a>Como definir um tipo de item do projeto do SharePoint
  Define um tipo de item de projeto quando você deseja criar um item de projeto do SharePoint personalizado. Para obter mais informações, consulte [definindo tipos de Item de projeto do SharePoint de personalizado](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
### <a name="to-define-a-project-item-type"></a>Para definir um tipo de item de projeto  
  
1.  Crie um projeto de biblioteca de classes.  
  
2.  Adicione referências aos assemblies a seguir:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Crie uma nova classe que implemente a interface <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.  
  
4.  Adicione os seguintes atributos à classe:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Este atributo permite que o Visual Studio para descobrir e carregar sua <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementação. Passar o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> tipo para o construtor de atributo.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Em uma definição de tipo de item de projeto, este atributo especifica o identificador de cadeia de caracteres para o novo item de projeto. É recomendável que você use o formato *nome da empresa*. *nome do recurso* para certificar-se de que todos os itens de projeto tem um nome exclusivo.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>. Esse atributo especifica o ícone a ser exibido para este item de projeto no **Gerenciador de soluções**. Esse atributo é opcional. Se você não aplicá-lo à sua classe, o Visual Studio exibe um ícone padrão para o item de projeto. Se você definir esse atributo, passe o nome totalmente qualificado de um ícone ou bitmap incorporado no seu assembly.  
  
5.  Na implementação do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> método, use membros o *projectItemTypeDefinition* parâmetro para definir o comportamento do tipo de item de projeto. Esse parâmetro é um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> objeto que fornece acesso para os eventos definidos no <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents> interfaces. Para acessar uma instância específica do seu tipo de item de projeto, tratar <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventos como <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como definir um tipo de item de projeto simples. Este tipo de item de projeto grava uma mensagem para o **saída** janela e **lista de erros** janela quando um usuário adiciona um item de projeto desse tipo para um projeto.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/projectitemtype.vb#2)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/projectitemtype.cs#2)]  
  
 Este exemplo usa o serviço de projeto do SharePoint para gravar a mensagem para o **saída** janela e **lista de erros** janela. Para obter mais informações, consulte [usando o serviço de projeto do SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer referências para os seguintes assemblies:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-project-item"></a>Implantando o Item de projeto  
 Para habilitar outros desenvolvedores a usar o item de projeto, crie um modelo de projeto ou um modelo de item de projeto. Para obter mais informações, consulte [criando modelos de Item e modelos de projeto do SharePoint para itens de projeto](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Para implantar o item de projeto, criar um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacote de extensão (VSIX) para o assembly, o modelo e outros arquivos que você quer distribuir com o item de projeto. Para obter mais informações, consulte [implantação de extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Consulte também  
 [Definindo tipos de Item de projeto do SharePoint personalizado](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Criando modelos de projeto e modelos de Item para itens de projeto do SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Passo a passo: Criando um Item de projeto de ação personalizada com um modelo de Item, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Passo a passo: Criando um Item de projeto da coluna de Site com um modelo de projeto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Como: adicionar uma propriedade a um tipo de Item de projeto do SharePoint personalizado](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Como adicionar um item de menu de atalho a um tipo de item de projeto personalizado do SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)  
  
  