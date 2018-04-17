---
title: 'Como: recuperar programaticamente caracteres iniciais e finais em intervalos | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a79112e80885dfd64b85a90125ea059277725d33
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Como recuperar caracteres iniciais e finais em intervalos programaticamente
  Este exemplo demonstra como você pode recuperar as posições de caractere das posições inicial e final de um intervalo.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>Para recuperar caracteres iniciais e finais de um intervalo em uma personalização no nível do documento  
  
1.  Obter os valores da <xref:Microsoft.Office.Interop.Word.Range.Start%2A> e <xref:Microsoft.Office.Interop.Word.Range.End%2A> propriedades do <xref:Microsoft.Office.Interop.Word.Range> objeto. O exemplo de código a seguir obtém a posição de início e término da segunda frase no documento. Para usar este exemplo de código, executá-la na `ThisDocument` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]  
  
### <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-an-vsto-add-in"></a>Para recuperar caracteres iniciais e finais de um intervalo usando um suplemento do VSTO  
  
1.  Obter os valores da <xref:Microsoft.Office.Interop.Word.Range.Start%2A> e <xref:Microsoft.Office.Interop.Word.Range.End%2A> propriedades do <xref:Microsoft.Office.Interop.Word.Range> objeto. O exemplo de código a seguir obtém a posição de início e término da segunda frase no documento ativo. Para usar este exemplo de código, executá-la na `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: definir programaticamente e selecionar intervalos em documentos](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Como: estender a intervalos em documentos programaticamente](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Como: programaticamente redefinir intervalos em Word documentos](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Como: programaticamente recolher intervalos ou seleções em documentos](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Como: excluir programaticamente marcas de parágrafo ao criar intervalos](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Como contar caracteres em documentos de forma programática](../vsto/how-to-programmatically-count-characters-in-documents.md)  
  
  