---
title: 'Como: exibir documentos em Visualizar impressão programaticamente | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bca26eb30ed9c468d154dbba6e2f126d3c61050f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Como exibir documentos em Visualizar Impressão programaticamente
  Se sua solução gera um relatório, você talvez queira exibir o relatório para o usuário no modo de visualização de impressão.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="procedures-for-document-level-customizations"></a>Procedimentos para personalizações no nível do documento  
  
#### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Para exibir um documento na visualização de impressão chamando o método PrintPreview  
  
1.  Chamar o <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> método o <xref:Microsoft.Office.Tools.Word.Document> classe. Para usar este exemplo de código, executá-la na `ThisDocument` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#13)]  
  
#### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Para exibir um documento na visualização de impressão, definindo a propriedade PrintPreview  
  
1.  Definir o <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> propriedade o <xref:Microsoft.Office.Interop.Word.Application> objeto para **true**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="procedures-for-vsto-add-ins"></a>Procedimentos para suplementos VSTO  
  
#### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Para exibir um documento na visualização de impressão chamando o método PrintPreview  
  
1.  Chamar o <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> método o <xref:Microsoft.Office.Interop.Word.Document> que você deseja visualizar. Para usar este exemplo de código, executá-la na `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#13)]  
  
#### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Para exibir um documento na visualização de impressão, definindo a propriedade PrintPreview  
  
1.  Definir o <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> propriedade o <xref:Microsoft.Office.Interop.Word.Application> objeto para **true**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: imprimir documentos programaticamente](../vsto/how-to-programmatically-print-documents.md)   
 [Como: abrir documentos existentes programaticamente](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Como criar novos documentos de forma programática](../vsto/how-to-programmatically-create-new-documents.md)  
  
  