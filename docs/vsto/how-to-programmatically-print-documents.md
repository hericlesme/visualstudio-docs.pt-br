---
title: 'Como: imprimir documentos programaticamente | Microsoft Docs'
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
- Word [Office development in Visual Studio], printing documents
- documents [Office development in Visual Studio], printing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9aa3e4b21aedff239aabde616b12a4f59281ec0a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-print-documents"></a>Como imprimir documentos programaticamente
  Você pode imprimir todo um documento do Microsoft Office Word ou parte de um documento, para a impressora padrão.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="printing-a-document-that-is-part-of-a-document-level-customization"></a>Imprimir um documento que faz parte de uma personalização no nível do documento  
  
#### <a name="to-print-the-entire-document"></a>Para imprimir o documento inteiro  
  
1.  Chamar o <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> método o `ThisDocument` classe em seu projeto para imprimir o documento inteiro. Para usar esse exemplo, execute o código na classe `ThisDocument`.  
  
     [!code-vb[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#11)]  
  
#### <a name="to-print-the-current-page-of-the-document"></a>Para imprimir a página atual do documento  
  
1.  Chamar o <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> método o `ThisDocument` classe em seu projeto e especifique que uma cópia da página atual seja impresso. Para usar esse exemplo, execute o código na classe `ThisDocument`.  
  
     [!code-vb[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#12)]  
  
## <a name="printing-a-document-by-using-an-vsto-add-in"></a>Imprimir um documento usando um suplemento do VSTO  
  
#### <a name="to-print-an-entire-document"></a>Para imprimir um documento inteiro  
  
1.  Chamar o <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> método o <xref:Microsoft.Office.Interop.Word.Document> objeto que você deseja imprimir. O exemplo de código a seguir imprime o documento ativo. Para usar este exemplo, execute o código do `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#11)]  
  
#### <a name="to-print-the-current-page-of-a-document"></a>Para imprimir a página atual de um documento  
  
1.  Chamar o <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> método o <xref:Microsoft.Office.Interop.Word.Document> objeto que você deseja imprimir e especificar que uma cópia da página atual seja impresso. O exemplo de código a seguir imprime o documento ativo. Para usar este exemplo, execute o código do `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#12)]  
  
## <a name="see-also"></a>Consulte também  
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  