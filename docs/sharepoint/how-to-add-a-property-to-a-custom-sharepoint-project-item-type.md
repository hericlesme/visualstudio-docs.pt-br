---
title: 'Como: adicionar uma propriedade a um tipo de Item de projeto do SharePoint personalizado | Microsoft Docs'
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
ms.assetid: 47e940f6-1779-4530-aea6-c43a370c544f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6d7a69673a4cd195d04c9b72a9ead0659600fb3d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-property-to-a-custom-sharepoint-project-item-type"></a>Como adicionar uma propriedade a um tipo de item de projeto do SharePoint personalizado
  Quando você define um tipo de item de projeto do SharePoint personalizado, você pode adicionar uma propriedade para o item de projeto. A propriedade aparece no **propriedades** janela quando o item de projeto é selecionado na **Gerenciador de soluções**.  
  
 As etapas a seguir pressupõem que você já definiu seu próprio tipo de item de projeto do SharePoint. Para obter mais informações, consulte [como: definir um tipo de Item de projeto do SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### <a name="to-add-a-property-to-a-definition-of-a-project-item-type"></a>Para adicionar uma propriedade a uma definição de um tipo de item de projeto  
  
1.  Defina uma classe com uma propriedade pública que representa a propriedade que você está adicionando ao tipo de item de projeto personalizados. Se você quiser adicionar várias propriedades a um tipo de item de projeto personalizado, você pode definir todas as propriedades na mesma classe ou em classes diferentes.  
  
2.  No <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> método de seu <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementação, o identificador de <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> eventos do *projectItemTypeDefinition* parâmetro.  
  
3.  No manipulador de eventos para o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento, adicionar uma instância de sua classe de propriedades personalizadas para o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> coleção de parâmetro dos argumentos do evento.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como adicionar uma propriedade chamada **exemplo de propriedade** para um personalizado item tipo de projeto.  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#11)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#11](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#11)]  
  
### <a name="understanding-the-code"></a>Noções básicas sobre o código  
 Para garantir que a mesma instância do `CustomProperties` classe é usada sempre que o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento ocorrer, o exemplo de código salva o objeto de propriedades para o <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriedade do tempo de item do primeiro projeto esse evento ocorre. O código recupera esse objeto sempre que esse evento ocorre novamente. Para obter mais informações sobre como usar o <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriedade ao salvar dados com itens de projeto, consulte [associando dados personalizados com extensões de ferramentas do SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Para manter as alterações para o valor da propriedade, o **definir** acessador para `ExampleProperty` salva o novo valor para o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriedade do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objeto que a propriedade está associada. Para obter mais informações sobre como usar o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriedade persistir dados com itens de projeto, consulte [salvando dados em extensões do sistema de projeto do SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>Especificar o comportamento de propriedades personalizadas  
 Você pode definir como uma propriedade personalizada é exibida e o comportamento de **propriedades** janela aplicando atributos do <xref:System.ComponentModel> namespace para a definição da propriedade. Os seguintes atributos são úteis em vários cenários:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Especifica o nome da propriedade que aparece no **propriedades** janela.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Especifica a cadeia de caracteres de descrição que aparece na parte inferior da **propriedades** janela quando a propriedade é selecionada.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Especifica o valor padrão da propriedade.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Especifica uma conversão personalizada entre a cadeia de caracteres que é exibida no **propriedades** janela e um valor de propriedade de cadeia de caracteres não.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Especifica um editor personalizado para usar para modificar a propriedade.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Esses exemplos de código requerem um projeto de biblioteca de classes com as referências para os seguintes assemblies:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-project-item"></a>Implantando o Item de projeto  
 Para habilitar outros desenvolvedores a usar o item de projeto, crie um modelo de projeto ou um modelo de item de projeto. Para obter mais informações, consulte [criando modelos de Item e modelos de projeto do SharePoint para itens de projeto](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Para implantar o item de projeto, criar um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacote de extensão (VSIX) para o assembly, o modelo e outros arquivos que você quer distribuir com o item de projeto. Para obter mais informações, consulte [implantação de extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como: definir um tipo de Item de projeto do SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [Como: adicionar um Item de Menu de atalho para um tipo de Item de projeto do SharePoint personalizado](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Definindo tipos de item de projeto personalizados do SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  