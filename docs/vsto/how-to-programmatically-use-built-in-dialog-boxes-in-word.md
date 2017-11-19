---
title: "Como: programaticamente, Use as caixas de diálogo integradas no Word | Microsoft Docs"
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
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
ms.assetid: 0c7e4338-dead-4444-868b-3b0212368455
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7dd7d81837699aedd1c6c61d0cb0d9e2e9a64db4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Como usar caixas de diálogo integradas no Word programaticamente
  Ao trabalhar com o Microsoft Office Word, há ocasiões em que você precisa para exibir caixas de diálogo de entrada do usuário. Embora você possa criar seus próprios, você também poderá usar a abordagem de usando as caixas de diálogo integradas no Word, que são expostas no <xref:Microsoft.Office.Interop.Word.Dialogs> coleção do <xref:Microsoft.Office.Interop.Word.Application> objeto. Isso permite que você acesse mais de 200 caixas de diálogo internas, que são representadas como enumerações.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="displaying-dialog-boxes"></a>Exibindo caixas de diálogo  
 Para exibir uma caixa de diálogo, use um dos valores da <xref:Microsoft.Office.Interop.Word.WdWordDialog> enumeração para criar um <xref:Microsoft.Office.Interop.Word.Dialog> objeto que representa a caixa de diálogo que você deseja exibir. Em seguida, chame o <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> método o <xref:Microsoft.Office.Interop.Word.Dialog> objeto.  
  
 O exemplo de código a seguir demonstra como exibir o **abrir arquivo** caixa de diálogo. Para usar este exemplo, executá-la na `ThisDocument` ou `ThisAddIn` classe em seu projeto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]  
  
### <a name="accessing-dialog-box-members-that-are-available-through-late-binding"></a>Acessando membros de caixa de diálogo que estão disponíveis por meio de associação tardia  
 Algumas propriedades e métodos de caixas de diálogo do Word estão disponíveis apenas por meio de associação tardia. No Visual Basic, projetos onde **Option Strict** está ativada, você deve usar reflexão para acessar esses membros. Para obter mais informações, consulte [associação tardia em soluções do Office](../vsto/late-binding-in-office-solutions.md).  
  
 O exemplo de código a seguir demonstra como usar o **nome** propriedade do **abrir arquivo** caixa de diálogo no Visual Basic projetos onde **Option Strict** é ou desativar no Visual c# projetos que visam o [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Para usar este exemplo, executá-la na `ThisDocument` ou `ThisAddIn` classe em seu projeto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 O exemplo de código a seguir demonstra como usar reflexão para acessar o **nome** propriedade o **abrir arquivo** caixa de diálogo no Visual Basic projetos onde **Option Strict** é no. Para usar este exemplo, executá-la na `ThisDocument` ou `ThisAddIn` classe em seu projeto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: usar o caixas de diálogo do Word no modo oculto programaticamente](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)   
 [Visão geral do modelo de objeto do Word](../vsto/word-object-model-overview.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Instrução Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Reflexão (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Reflexão (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
  
  