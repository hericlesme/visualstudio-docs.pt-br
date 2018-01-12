---
title: 'Como: estender programaticamente intervalos em documentos | Microsoft Docs'
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
- ranges, extending
- documents [Office development in Visual Studio], extending ranges
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 81d3535f7f4e449c5cb56bea78a255b5388d6e94
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-extend-ranges-in-documents"></a>Como estender intervalos em documentos programaticamente
  Depois de definir um <xref:Microsoft.Office.Interop.Word.Range> do objeto em um documento do Word do Microsoft Office, você alterar seus pontos inicial e final usando o <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> e <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> métodos. O <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> e <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> métodos usam os mesmo dois argumentos, *unidade* e *contagem*. O *contagem* é o número de unidades para mover e o *unidade* argumento pode ser um dos seguintes <xref:Microsoft.Office.Interop.Word.WdUnits> valores:  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdCharacter>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdWord>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdSentence>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdParagraph>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdSection>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdStory>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdCell>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdColumn>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdRow>  
  
-   <xref:Microsoft.Office.Interop.Word.WdUnits.wdTable>  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 O exemplo a seguir define um intervalo de sete caracteres. Ele move a posição de início dos caracteres intervalo sete, em seguida, após a posição inicial original. Como a posição final do intervalo também foi sete caracteres após a posição inicial, o resultado é um intervalo que consiste em caracteres. O código, em seguida, move os caracteres de sete posição final após a posição final atual.  
  
### <a name="to-extend-a-range"></a>Para estender um intervalo  
  
1.  Defina um intervalo de caracteres. Para obter mais informações, consulte [como: definir programaticamente e selecionar intervalos em documentos](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).  
  
     O exemplo de código a seguir pode ser usado em uma personalização no nível do documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#39)]  
  
     O exemplo de código a seguir pode ser usado em um suplemento do VSTO. Este exemplo usa o documento ativo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#39)]  
  
2.  Use o <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> método o <xref:Microsoft.Office.Interop.Word.Range> objeto para mover a posição de início do intervalo.  
  
     [!code-vb[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#40)]
     [!code-csharp[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#40)]  
  
3.  Use o <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> método o <xref:Microsoft.Office.Interop.Word.Range> objeto para mover a posição final do intervalo.  
  
     [!code-vb[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#41)]
     [!code-csharp[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#41)]  
  
## <a name="document-level-customization-code"></a>Código de personalização de nível de documento  
  
#### <a name="to-extend-a-range-in-a-document-level-customization"></a>Para estender um intervalo em uma personalização no nível do documento  
  
1.  O exemplo a seguir mostra o código completo para uma personalização no nível do documento. Para usar esse código, executá-la na `ThisDocument` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#38)]  
  
## <a name="vsto-add-in-code"></a>Código de suplemento do VSTO  
  
#### <a name="to-extend-a-range-in-an-application-level-vsto-add-in"></a>Para estender um intervalo de um suplemento do VSTO do nível do aplicativo  
  
1.  O exemplo a seguir mostra o código completo para um suplemento do VSTO. Para usar esse código, executá-la na `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#38)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: programaticamente redefinir intervalos em Word documentos](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Como: programaticamente recolher intervalos ou seleções em documentos](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Como: definir programaticamente e selecionar intervalos em documentos](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Como: recuperar programaticamente caracteres iniciais e finais em intervalos](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Como excluir marcas de parágrafo ao criar intervalos de forma programática](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  