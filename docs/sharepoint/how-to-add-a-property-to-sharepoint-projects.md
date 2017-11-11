---
title: 'How to: Add a Property to SharePoint Projects | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.prod: visual-studio-dev14
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
ms.assetid: c5eb4900-c35f-490a-b856-bf167da2d293
caps.latest.revision: 17
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 6ef0b253acb4f6347627e1869e9b2f7f28dcc38f
ms.contentlocale: pt-br
ms.lasthandoff: 08/30/2017

---
# <a name="how-to-add-a-property-to-sharepoint-projects"></a>How to: Add a Property to SharePoint Projects
  You can use a project extension to add a property to any SharePoint project. The property appears in the **Properties** window when the project is selected in **Solution Explorer**.  
  
 The following steps assume that you have already created a project extension. For more information, see [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### <a name="to-add-a-property-to-a-sharepoint-project"></a>To add a property to a SharePoint project  
  
1.  Define a class with a public property that represents the property you are adding to SharePoint projects. If you want to add multiple properties, you can define all the properties in the same class or in different classes.  
  
2.  In the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> method of your <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementation, handle the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> event of the *projectService* parameter.  
  
3.  In the event handler for the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> event, add an instance of your properties class to the <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectPropertiesRequestedEventArgs.PropertySources%2A> collection of the event arguments parameter.  
  
## <a name="example"></a>Example  
 The following code example demonstrates how to add two properties to SharePoint projects. One property persists its data in the project user option file (the .csproj.user file or .vbproj.user file). The other property persists its data in the project file (.csproj file or .vbproj file).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#1)] [!code-csharp[SpExt_SPCustomPrjProperty#1](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#1)]  
  
### <a name="understanding-the-code"></a>Understanding the Code  
 To ensure that the same instance of the `CustomProjectProperties` class is used each time the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> event occurs, the code example adds the properties object to the <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> property of the project the first time this event occurs. The code retrieves this object whenever this event occurs again. For more information about using the <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> property to associate data with projects, see [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
 To persist changes to the property values, the **set** accessors for the properties use the following APIs:  
  
-   `CustomUserFileProperty` uses the <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> property to save its value to the project user option file.  
  
-   `CustomProjectFileProperty` uses the <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> method to save its value to the project file.  
  
 For more information about persisting data in these files, see [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
### <a name="specifying-the-behavior-of-custom-properties"></a>Specifying the Behavior of Custom Properties  
 You can define how a custom property appears and behaves in the **Properties** window by applying attributes from the <xref:System.ComponentModel> namespace to the property definition. The following attributes are useful in many scenarios:  
  
-   <xref:System.ComponentModel.DisplayNameAttribute>: Specifies the name of the property that appears in the **Properties** window.  
  
-   <xref:System.ComponentModel.DescriptionAttribute>: Specifies the description string that appears in the bottom of the **Properties** window when the property is selected.  
  
-   <xref:System.ComponentModel.DefaultValueAttribute>: Specifies the default value of the property.  
  
-   <xref:System.ComponentModel.TypeConverterAttribute>: Specifies a custom conversion between the string that is displayed in the **Properties** window and a non-string property value.  
  
-   <xref:System.ComponentModel.EditorAttribute>: Specifies a custom editor to use to modify the property.  
  
## <a name="compiling-the-code"></a>Compiling the Code  
 This example requires references to the following assemblies:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.Shell  
  
-   Microsoft.VisualStudio.Shell.Interop  
  
-   Microsoft.VisualStudio.Shell.Interop.8.0  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Deploying the Extension  
 To deploy the extension, create a [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] extension (VSIX) package for the assembly and any other files that you want to distribute with the extension. For more information, see [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>See Also  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  