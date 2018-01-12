---
title: "Como: adicionar comentários a texto em documentos programaticamente | Microsoft Docs"
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
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2702d8aed4dce16a2dde1c42b2b1410ebded14e3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>Como adicionar comentários ao texto em documentos programaticamente
  A propriedade de comentários da classe do documento adiciona um comentário a um intervalo de texto em um documento do Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 O exemplo a seguir adiciona um comentário ao primeiro parágrafo no documento.  
  
### <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>Para adicionar um novo comentário ao texto em uma personalização no nível do documento  
  
1.  Chamar o <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> método o <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> propriedade e forneça um intervalo e o texto do comentário. Para usar o exemplo de código a seguir, executá-la na `ThisDocument` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#118)]  
  
### <a name="to-add-a-new-comment-to-text-in-an-vsto-add-in"></a>Para adicionar um novo comentário ao texto em um suplemento do VSTO  
  
1.  Chamar o <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> método o <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> propriedade e forneça um intervalo e o texto do comentário.  
  
     O exemplo de código a seguir adiciona um comentário para o documento ativo. Para usar este exemplo, executá-la na `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#118)]  
  
## <a name="robust-programming"></a>Programação robusta  
 Para alterar as iniciais do usuário que o Word adiciona comentários, use o <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> propriedade.  
  
## <a name="see-also"></a>Consulte também  
 [Como: remover todos os comentários de documentos programaticamente](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)   
 [Item de host do documento](../vsto/document-host-item.md)  
  
  