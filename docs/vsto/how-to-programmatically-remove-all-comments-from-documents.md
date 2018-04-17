---
title: 'Como: remover todos os comentários de documentos programaticamente | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], removing comments
- comments, removing from documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 19c713356a8949261524eda9f44fee8fae9f9f21
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>Como remover todos os comentários de documentos programaticamente
  Use o método DeleteAllComments para remover todos os comentários de um documento do Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>Para remover todos os comentários de um documento que faz parte de uma personalização no nível do documento  
  
1.  Chamar o <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> método o `ThisDocument` classe em seu projeto. Para usar este exemplo de código, executá-la na `ThisDocument` classe.  
  
     [!code-vb[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#119)]  
  
### <a name="to-remove-all-comments-from-a-document-by-using-an-vsto-add-in"></a>Para remover todos os comentários de um documento usando um suplemento do VSTO  
  
1.  Chamar o <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> método o <xref:Microsoft.Office.Interop.Word.Document> do qual você deseja remover os comentários.  
  
     O exemplo de código a seguir remove todos os comentários do documento ativo. Para usar este exemplo de código, executá-la na `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#119)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: adicionar comentários a texto em documentos programaticamente](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)   
 [Item de host do documento](../vsto/document-host-item.md)  
  
  