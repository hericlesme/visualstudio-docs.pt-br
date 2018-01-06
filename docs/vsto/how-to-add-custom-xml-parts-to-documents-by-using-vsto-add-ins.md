---
title: 'Como: adicionar partes XML personalizadas aos documentos usando suplementos VSTO | Microsoft Docs'
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
- add-ins [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- PowerPoint [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- custom XML parts [Office development in Visual Studio], adding
- documents [Office development in Visual Studio], custom XML parts
- application-level add-ins [Office development in Visual Studio], custom XML parts
ms.assetid: 872d2beb-193b-49f9-9a7b-dcebab91a73b
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4f7c88ca0ef06ea74f6963166a2b6f421058c0da
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins"></a>Como adicionar partes XML personalizadas aos documentos usando suplementos VSTO
  Você pode armazenar dados XML nos seguintes tipos de documentos, criando uma parte XML personalizada em um suplemento do VSTO:  
  
-   Uma pasta de trabalho do Microsoft Office Excel.  
  
-   Um documento do Microsoft Office Word.  
  
-   Uma apresentação do PowerPoint do Microsoft Office.  
  
 Para obter mais informações, consulte [visão geral de partes de XML personalizado](../vsto/custom-xml-parts-overview.md).  
  
 **Aplica-se a:** as informações neste tópico se aplicam a projetos no nível de aplicativo para Excel, PowerPoint e Word. Para obter mais informações, consulte [recursos disponibilizados pelo aplicativo do Office e pelo tipo de projeto](../vsto/features-available-by-office-application-and-project-type.md).  
  
### <a name="to-add-a-custom-xml-part-to-an-excel-workbook"></a>Para adicionar uma parte XML personalizada a uma pasta de trabalho do Excel  
  
1.  Adicionar um novo <xref:Microsoft.Office.Core.CustomXMLPart> o objeto para o <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> coleção na pasta de trabalho. O <xref:Microsoft.Office.Core.CustomXMLPart> contém a cadeia de caracteres XML que você deseja armazenar na pasta de trabalho.  
  
     O exemplo de código a seguir adiciona uma parte XML personalizada para uma pasta de trabalho especificada.  
  
     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/VisualBasic/trin_addcustomxmlpartexcelapplevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartExcelAppLevel/ThisAddIn.cs#1)]  
  
2.  Adicionar o `AddCustomXmlPartToWorkbook` método para o `ThisAddIn` classe em um projeto de suplemento do VSTO para Excel.  
  
3.  Chame o método de outro código no seu projeto. Por exemplo, para criar a parte XML personalizada quando o usuário abre uma pasta de trabalho, chame o método de um manipulador de eventos para o <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen> evento.  
  
### <a name="to-add-a-custom-xml-part-to-a-word-document"></a>Para adicionar uma parte XML personalizada para um documento do Word  
  
1.  Adicionar um novo <xref:Microsoft.Office.Core.CustomXMLPart> o objeto para o <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> coleção no documento. O <xref:Microsoft.Office.Core.CustomXMLPart> contém a cadeia de caracteres XML que você deseja armazenar no documento.  
  
     O exemplo de código a seguir adiciona uma parte XML personalizada a um documento especificado.  
  
     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.vb#1)]
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartWordAppLevel/ThisAddIn.cs#1)]  
  
2.  Adicionar o `AddCustomXmlPartToDocument` método para o `ThisAddIn` classe em um projeto de suplemento do VSTO para Word.  
  
3.  Chame o método de outro código no seu projeto. Por exemplo, para criar a parte XML personalizada quando o usuário abre um documento, chame o método de um manipulador de eventos para o <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> evento.  
  
### <a name="to-add-a-custom-xml-part-to-a-powerpoint-presentation"></a>Para adicionar uma parte XML personalizada para uma apresentação do PowerPoint  
  
1.  Adicionar um novo <xref:Microsoft.Office.Core.CustomXMLPart> o objeto para o <xref:Microsoft.Office.Interop.PowerPoint._Presentation.CustomXMLParts%2A> coleção da apresentação. O <xref:Microsoft.Office.Core.CustomXMLPart> contém a cadeia de caracteres XML que você deseja armazenar a apresentação.  
  
     O exemplo de código a seguir adiciona uma parte XML personalizada para uma apresentação especificada.  
  
     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/CSharp/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../vsto/codesnippet/VisualBasic/Trin_AddCustomXmlPartPowerPointAppLevel/ThisAddIn.vb#1)]  
  
2.  Adicionar o `AddCustomXmlPartToPresentation` método para o `ThisAddIn` classe em um projeto de suplemento do VSTO para PowerPoint.  
  
3.  Chame o método de outro código no seu projeto. Por exemplo, para criar a parte XML personalizada quando o usuário abre uma apresentação, chame o método de um manipulador de eventos para o <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen> evento.  
  
## <a name="robust-programming"></a>Programação robusta  
 Para simplificar, este exemplo usa uma cadeia de caracteres XML que é definida como uma variável local no método. Normalmente, você deverá obter o XML de uma fonte externa, como um arquivo ou um banco de dados.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de partes XML personalizadas](../vsto/custom-xml-parts-overview.md)   
 [Como adicionar partes XML personalizadas no nível do documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
  