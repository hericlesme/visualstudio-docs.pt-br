---
title: 'Como: criar e modificar propriedades de documento personalizadas | Microsoft Docs'
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
- custom document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5d081beb3422126f6ccf7484cb08e7fa43da8874
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Como criar e modificar propriedades de documento personalizadas
  Aplicativos do Microsoft Office listados acima fornecem propriedades internas que são armazenadas com documentos. Além disso, você pode criar e modificar propriedades de documento personalizadas se há informações adicionais que você deseja armazenar com o documento.  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
 Use a propriedade CustomDocumentProperties de um documento para trabalhar com propriedades personalizadas. Por exemplo, em um projeto de nível de documento do Microsoft Office Excel, use o <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> propriedade o `ThisWorkbook` classe. Em um projeto do suplemento do VSTO para Excel, use o <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> propriedade de um <xref:Microsoft.Office.Interop.Excel.Workbook> objeto. Essas propriedades retornam um <xref:Microsoft.Office.Core.DocumentProperties> objeto, que é uma coleção de <xref:Microsoft.Office.Core.DocumentProperty> objetos. Você pode usar o `Item` propriedade da coleção para recuperar uma propriedade específica, por nome ou índice dentro da coleção.  
  
 O exemplo a seguir demonstra como adicionar uma propriedade personalizada em uma personalização de nível de documento para Excel e atribuir a ela um valor.  
  
 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração de vídeo relacionada, consulte [como fazer i: acesso e manipular propriedades de documento personalizadas no Microsoft Word?](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
## <a name="example"></a>Exemplo  
 [!code-vb[Trin_VstcoreProgramming#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#6)]
 [!code-csharp[Trin_VstcoreProgramming#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#6)]  
  
## <a name="robust-programming"></a>Programação robusta  
 Tentativa de acesso a `Value` propriedade para propriedades indefinidas gera uma exceção.  
  
## <a name="see-also"></a>Consulte também  
 [Suplementos de programação para o VSTO](../vsto/programming-vsto-add-ins.md)   
 [Personalizações no nível do documento da programação](../vsto/programming-document-level-customizations.md)   
 [Como ler e gravar em propriedades do documento](../vsto/how-to-read-from-and-write-to-document-properties.md)  
  
  