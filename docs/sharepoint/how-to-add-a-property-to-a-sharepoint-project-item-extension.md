---
title: "Como: adicionar uma propriedade a uma extensão de Item de projeto do SharePoint | Microsoft Docs"
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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1b096a1d524a1702d7fae01d35fb08e2fa697c70
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-property-to-a-sharepoint-project-item-extension"></a>Como adicionar uma propriedade a uma extensão de item de projeto do SharePoint
  Você pode usar uma extensão de item de projeto para adicionar uma propriedade a qualquer item de projeto do SharePoint que já está instalado no Visual Studio. A propriedade aparece no **propriedades** janela quando o item de projeto é selecionado na **Gerenciador de soluções**.  
  
 As etapas a seguir pressupõem que você já tenha criado uma extensão de item de projeto. Para obter mais informações, consulte [como: criar uma extensão de Item de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### <a name="to-add-a-property-to-a-project-item-extension"></a>Para adicionar uma propriedade a uma extensão de item de projeto  
  
1.  Defina uma classe com uma propriedade pública que representa a propriedade que você está adicionando a um tipo de item de projeto. Se você quiser adicionar várias propriedades a um tipo de item de projeto, você pode definir todas as propriedades na mesma classe ou em classes diferentes.  
  
2.  No <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> método de seu <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> implementação, o identificador de <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> eventos do *projectItemType* parâmetro.  
  
3.  No manipulador de eventos para o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento, adicionar uma instância de sua classe de propriedades para o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemPropertiesRequestedEventArgs.PropertySources%2A> coleção de parâmetro dos argumentos do evento.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como adicionar uma propriedade chamada **exemplo de propriedade** para o item de projeto do receptor de evento.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemextensionproperty.cs#8)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#8](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemextensionproperty.vb#8)]  
  
### <a name="understanding-the-code"></a>Noções básicas sobre o código  
 Para garantir que a mesma instância do `CustomProperties` classe é usada sempre que o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemPropertiesRequested> evento ocorre, o exemplo de código adiciona o objeto de propriedades para o <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriedade do tempo de item do primeiro projeto esse evento ocorre. O código recupera esse objeto sempre que esse evento ocorre novamente. Para obter mais informações sobre como usar o <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propriedade para associar dados a itens de projeto, consulte [associando dados personalizados com extensões de ferramentas do SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 Para manter as alterações para o valor da propriedade, o **definir** acessador para `ExampleProperty` salva o novo valor para o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriedade do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objeto que a propriedade está associada. Para obter mais informações sobre como usar o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriedade persistir dados com itens de projeto, consulte [salvando dados em extensões do sistema de projeto do SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>Especificar o comportamento de propriedades personalizadas  
 Você pode definir como uma propriedade personalizada é exibida e o comportamento de **propriedades** janela aplicando atributos do <xref:System.ComponentModel> namespace para a definição da propriedade. Os seguintes atributos são úteis em vários cenários:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Especifica o nome da propriedade que aparece no **propriedades** janela.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Especifica a cadeia de caracteres de descrição que aparece na parte inferior da **propriedades** janela quando a propriedade é selecionada.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Especifica o valor padrão da propriedade.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Especifica uma conversão personalizada entre a cadeia de caracteres que é exibida no **propriedades** janela e um valor de propriedade de cadeia de caracteres não.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Especifica um editor personalizado para usar para modificar a propriedade.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Esses exemplos exigem um projeto de biblioteca de classes com as referências para os seguintes assemblies:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Implantando a extensão  
 Para implantar a extensão, criar um [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacote de extensão (VSIX) para o assembly e outros arquivos que você quer distribuir com a extensão. Para obter mais informações, consulte [implantação de extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar uma extensão de Item de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [Como: adicionar um Item de Menu de atalho para uma extensão de Item de projeto do SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)   
 [Estendendo itens de projeto do SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Instruções passo a passo: estendendo um tipo de item do projeto do SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  