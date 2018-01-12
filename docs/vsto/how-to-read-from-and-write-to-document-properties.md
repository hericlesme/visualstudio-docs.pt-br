---
title: 'Como: ler e gravar em Propriedades do documento | Microsoft Docs'
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
- Word [Office development in Visual Studio], document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
- Excel [Office development in Visual Studio], document properties
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1e2ac54009872aa8886b201007b60ec329a40a39
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-read-from-and-write-to-document-properties"></a>Como ler e gravar em propriedades do documento
  Você pode armazenar propriedades de documento junto com um documento. Aplicativos do Office fornecem uma série de propriedades internas, como autor, título e assunto. Este tópico mostra como definir propriedades de documento no Microsoft Office Excel e o Microsoft Office Word.  
  
 ![link para vídeo](../vsto/media/playvideo.gif "link para vídeo") para uma demonstração de vídeo relacionada, consulte [como fazer i: acesso e manipular propriedades de documento personalizadas no Microsoft Word?](http://go.microsoft.com/fwlink/?LinkId=136772).  
  
 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]  
  
## <a name="setting-document-properties-in-excel"></a>Definir propriedades do documento no Excel  
 Para trabalhar com propriedades internas no Excel, use as seguintes propriedades:  
  
-   Em um projeto de nível de documento, use o <xref:Microsoft.Office.Tools.Excel.Workbook.BuiltinDocumentProperties%2A> propriedade o `ThisWorkbook` classe.  
  
-   Em um projeto de suplemento do VSTO, use o <xref:Microsoft.Office.Interop.Excel._Workbook.BuiltinDocumentProperties%2A> propriedade de um <xref:Microsoft.Office.Interop.Excel.Workbook> objeto.  
  
 Essas propriedades retornam um <xref:Microsoft.Office.Core.DocumentProperties> objeto, que é uma coleção de <xref:Microsoft.Office.Core.DocumentProperty> objetos. Você pode usar o `Item` propriedade da coleção para recuperar uma propriedade específica, por nome ou índice dentro da coleção.  
  
 O exemplo de código a seguir mostra como alterar o interno **número de revisão** propriedade em um projeto no nível do documento.  
  
#### <a name="to-change-the-revision-number-property-in-excel"></a>Para alterar a propriedade de número de revisão no Excel  
  
1.  Atribua propriedades internas de documento a uma variável.  
  
     [!code-vb[Trin_VstcoreProgramming#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#7)]
     [!code-csharp[Trin_VstcoreProgramming#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#7)]  
  
2.  Incremento de `Revision Number` propriedade por um.  
  
     [!code-vb[Trin_VstcoreProgramming#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#8)]
     [!code-csharp[Trin_VstcoreProgramming#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#8)]  
  
## <a name="setting-document-properties-in-word"></a>Definindo propriedades de documento no Word  
 Para trabalhar com propriedades internas no Word, use as seguintes propriedades:  
  
-   Em um projeto de nível de documento, use o <xref:Microsoft.Office.Tools.Word.Document.BuiltInDocumentProperties%2A> propriedade o `ThisDocument` classe.  
  
-   Em um projeto de suplemento do VSTO, use o <xref:Microsoft.Office.Interop.Word._Document.BuiltInDocumentProperties%2A> propriedade de um <xref:Microsoft.Office.Interop.Word.Document> objeto.  
  
 Essas propriedades retornam um <xref:Microsoft.Office.Core.DocumentProperties> objeto, que é uma coleção de <xref:Microsoft.Office.Core.DocumentProperty> objetos. Você pode usar o `Item` propriedade da coleção para recuperar uma propriedade específica, por nome ou índice dentro da coleção.  
  
 O exemplo de código a seguir mostra como alterar o interno **assunto** propriedade em um projeto no nível do documento.  
  
#### <a name="to-change-the-subject-property"></a>Para alterar a propriedade de entidade  
  
1.  Atribua propriedades internas de documento a uma variável.  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreProgrammingWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#1)]  
  
2.  Alterar o `Subject` propriedade "White paper".  
  
     [!code-csharp[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingWordCS/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreProgrammingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingWordVB/ThisDocument.vb#2)]  
  
## <a name="robust-programming"></a>Programação robusta  
 Os exemplos assumem que você escreveu o código `ThisWorkbook` classe em um projeto de nível de documento para Excel e o `ThisDocument` classe em um projeto de nível de documento para Word.  
  
 Embora você estiver trabalhando com o Word e Excel e seus objetos, o Microsoft Office fornece a lista de propriedades de documento internas disponíveis. Tentativa de acessar uma propriedade indefinida gerará uma exceção.  
  
## <a name="see-also"></a>Consulte também  
 [Suplementos de programação para o VSTO](../vsto/programming-vsto-add-ins.md)   
 [Personalizações no nível do documento da programação](../vsto/programming-document-level-customizations.md)   
 [Como criar e modificar propriedades de documento personalizadas](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  