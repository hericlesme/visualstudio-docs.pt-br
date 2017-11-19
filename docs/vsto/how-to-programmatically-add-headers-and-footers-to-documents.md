---
title: "Como: adicionar programaticamente os cabeçalhos e rodapés a documentos | Microsoft Docs"
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
- headers, adding to Office documents
- documents [Office development in Visual Studio], adding headers
- documents [Office development in Visual Studio], adding footers
- footers, adding to documents
ms.assetid: c7a5cc8a-d8c0-48e9-81d3-108aa6bfbb74
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e6b8b95953257cefd7cf229cd094791793dfff1b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-add-headers-and-footers-to-documents"></a>Como adicionar cabeçalhos e rodapés a documentos programaticamente
  Você pode adicionar texto em cabeçalhos e rodapés de página no documento usando o <xref:Microsoft.Office.Interop.Word.Section.Headers%2A> propriedade e <xref:Microsoft.Office.Interop.Word.Section.Footers%2A> propriedade o <xref:Microsoft.Office.Interop.Word.Section>. Cada seção de um documento contém três cabeçalhos e rodapés de página:  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterPrimary>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterEvenPages>  
  
-   <xref:Microsoft.Office.Interop.Word.WdHeaderFooterIndex.wdHeaderFooterFirstPage>  
  
 Os procedimentos são diferentes para personalizações no nível do documento e suplementos do VSTO.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="document-level-customizations"></a>Personalizações no nível de documento  
 Para usar os exemplos de código a seguir, executá-los da `ThisDocument` classe em seu projeto.  
  
#### <a name="to-add-text-to-footers-in-the-document"></a>Para adicionar texto ao rodapés do documento  
  
1.  O exemplo de código a seguir define a fonte do texto a ser inserido no rodapé de cada seção do documento principal e, em seguida, insere o texto no rodapé.  
  
     [!code-vb[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomation#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#114)]  
  
#### <a name="to-add-text-to-headers-in-the-document"></a>Para adicionar texto ao cabeçalhos no documento  
  
1.  O exemplo de código a seguir adiciona um campo para mostrar o número da página em cada cabeçalho do documento e, em seguida, define o alinhamento do parágrafo para que o texto alinhado à direita do cabeçalho.  
  
     [!code-vb[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomation#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#116)]  
  
## <a name="vsto-add-ins"></a>Suplementos do VSTO  
 Para usar os exemplos de código a seguir, executá-los da `ThisAddIn` classe em seu projeto.  
  
#### <a name="to-add-text-to-footers-in-a-document"></a>Para adicionar texto ao rodapés de páginas em um documento  
  
1.  O exemplo de código a seguir define a fonte do texto a ser inserido no rodapé de cada seção do documento principal e, em seguida, insere o texto no rodapé. Este exemplo de código usa o documento ativo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#114)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#114](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#114)]  
  
#### <a name="to-add-text-to-headers-in-the-document"></a>Para adicionar texto ao cabeçalhos no documento  
  
1.  O exemplo de código a seguir adiciona um campo para mostrar o número da página em cada cabeçalho do documento e, em seguida, define o alinhamento do parágrafo para que o texto alinhado à direita do cabeçalho. Este exemplo de código usa o documento ativo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#116)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#116](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#116)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar novos documentos programaticamente](../vsto/how-to-programmatically-create-new-documents.md)   
 [Como: estender a intervalos em documentos programaticamente](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Como percorrer itens encontrados em documentos de forma programática](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)  
   