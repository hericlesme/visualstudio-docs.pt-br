---
title: Salvando dados em extensões do sistema de projeto do SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
helpviewer_keywords:
- SharePoint project items, saving string data
- project items [SharePoint development in Visual Studio], saving string data
- projects [SharePoint development in Visual Studio], saving string data
- SharePoint projects, saving string data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5efc6a11852c0f843415623f4a5ac94f9d3e392b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="saving-data-in-extensions-of-the-sharepoint-project-system"></a>Salvando dados em extensões do sistema de projeto do SharePoint
  Quando você estende o sistema de projeto do SharePoint, você pode salvar os dados de cadeia de caracteres que persiste depois que um projeto do SharePoint é fechado. Os dados são geralmente associados a um item de projeto específico ou com o projeto em si.  
  
 Se você tiver dados que não precisam manter, você pode adicionar dados a qualquer objeto no modelo de objeto do SharePoint ferramentas que implementa o <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject> interface. Para obter mais informações, consulte [associando dados personalizados com extensões de ferramentas do SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## <a name="saving-data-that-is-associated-with-a-project-item"></a>Salvando dados que está associado com um Item de projeto  
 Quando você tem dados que está associados um item de projeto do SharePoint específico, como o valor de uma propriedade que você adicionar a um item de projeto, você pode salvar os dados para o arquivo. spdata para o item de projeto. Para fazer isso, use o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriedade de um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> objeto. Os dados que você adicionar a esta propriedade é salvo no **ExtensionData** elemento no arquivo. spdata para o item de projeto. Para obter mais informações, consulte [elemento ExtensionData](../sharepoint/extensiondata-element.md).  
  
 O exemplo de código a seguir demonstra como usar o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> propriedade para salvar o valor de uma propriedade de cadeia de caracteres que é definido em um tipo de item de projeto do SharePoint personalizado. Para ver esse exemplo no contexto de um exemplo maior, consulte [como: adicionar uma propriedade a um tipo de Item de projeto de SharePoint personalizados](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypeproperty.vb#14)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypeproperty.cs#14)]  
  
## <a name="saving-data-that-is-associated-with-a-project"></a>Salvando dados que está associado com um projeto  
 Quando você tem dados de nível de projeto, como o valor de uma propriedade que você adicionar a projetos do SharePoint, você pode salvar os dados para o arquivo de projeto (arquivo. csproj ou. vbproj arquivo) ou o arquivo de opção de usuário do projeto (o. arquivo csproj.user ou. vbproj.user arquivo). O arquivo que você optar por salvar os dados depende de como você deseja que os dados a ser usado:  
  
-   Se você deseja que os dados estejam disponíveis para todos os desenvolvedores que abra o projeto do SharePoint, salve os dados para o arquivo de projeto. Este arquivo sempre é verificado bancos de dados de controle de origem, para que os dados deste arquivo estão disponíveis para outros desenvolvedores que check-out do projeto.  
  
-   Se você deseja que os dados estejam disponíveis somente para o desenvolvedor atual que abriu o projeto do SharePoint no Visual Studio, salve os dados para o arquivo de opção de usuário do projeto. Esse arquivo não é normalmente verificado bancos de dados de controle de origem, para que os dados neste arquivo não estão disponíveis para outros desenvolvedores que check-out do projeto.  
  
### <a name="saving-data-to-the-project-file"></a>Salvando dados para o arquivo de projeto  
 Para salvar os dados para o arquivo de projeto, converter um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> o objeto para um <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> objeto e, em seguida, use o <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> método. O exemplo de código a seguir demonstra como usar esse método para salvar o valor de uma propriedade de projeto para o arquivo de projeto. Para ver esse exemplo no contexto de um exemplo maior, consulte [como: adicionar uma propriedade a projetos SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#3)]
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#3)]  
  
 Para obter mais informações sobre como converter <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objetos para outros tipos de modelo de objeto de automação do Visual Studio ou o modelo de objeto de integração, consulte [converter entre SharePoint sistema de tipos de projeto e outros tipos de projeto Visual Studio ](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
### <a name="saving-data-to-the-project-user-option-file"></a>Salvando dados para o arquivo de opção de usuário do projeto  
 Para salvar os dados para o arquivo de opção de usuário do projeto, use o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> propriedade de um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objeto. O exemplo de código a seguir demonstra como usar essa propriedade para salvar o valor de uma propriedade de projeto para o arquivo de opção de usuário do projeto. Para ver esse exemplo no contexto de um exemplo maior, consulte [como: adicionar uma propriedade a projetos SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-vb[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/VisualBasic/customspproperty/customproperty.vb#2)]
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../sharepoint/codesnippet/CSharp/customspproperty/customproperty.cs#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Associando dados personalizados a extensões de ferramentas do SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Convertendo entre tipos de sistema de projeto do SharePoint e outros tipos de projeto do Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
  
  