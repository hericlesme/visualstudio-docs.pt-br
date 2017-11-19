---
title: 'Como: verificar a ortografia em documentos programaticamente | Microsoft Docs'
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
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
ms.assetid: 5bbe3a8d-fc65-4f57-bd63-5bb549dbc4bd
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ce7346e25253a4c98ce8bbb8b209ccef280793d1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Como verificar a ortografia em documentos programaticamente
  Para verificar a ortografia em um documento, use o <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> método. Esse método retorna um valor booliano que indica se o parâmetro fornecido está escrito corretamente.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Para verificar a ortografia e exibir resultados em uma caixa de mensagem  
  
1.  Chamar o <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> método e passá-lo em um intervalo de texto para verificar se há erros de ortografia. Para usar este exemplo de código, executá-la na `ThisDocument` ou `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: definir programaticamente e selecionar intervalos em documentos](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  