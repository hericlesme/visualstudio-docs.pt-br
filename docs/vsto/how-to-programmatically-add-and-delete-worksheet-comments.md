---
title: "Como: adicionar programaticamente e excluir os comentários da planilha | Microsoft Docs"
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
- ranges, comments
- worksheets, comments
- comments, worksheets
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9351dd018c2db4832db20a4abbdaa050f060793e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>Como adicionar e excluir comentários em planilhas programaticamente
  Programaticamente, você pode adicionar e excluir comentários em planilhas do Microsoft Office Excel. Comentários podem ser adicionados apenas a células único, não a intervalos de várias células.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="adding-and-deleting-a-comment-in-a-document-level-project"></a>Adicionando e excluindo um comentário em um projeto no nível de documento  
 Os exemplos a seguir pressupõem que há uma única célula <xref:Microsoft.Office.Tools.Excel.NamedRange> controle chamado `dateComment` em uma planilha denominada `Sheet1`.  
  
#### <a name="to-add-a-new-comment-to-a-named-range"></a>Para adicionar um novo comentário a um intervalo nomeado  
  
1.  Chamar o <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> método o <xref:Microsoft.Office.Tools.Excel.NamedRange> controlar e fornecer o texto de comentário. Esse código deve ser colocado no `Sheet1` classe.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#30)]  
  
#### <a name="to-delete-a-comment-from-a-named-range"></a>Para excluir um comentário de um intervalo nomeado  
  
1.  Verifique se existe um comentário no intervalo e excluí-lo. Esse código deve ser colocado no `Sheet1` classe.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#29)]  
  
## <a name="adding-and-deleting-a-comment-in-an-vsto-add-in-project"></a>Adicionando e excluindo um comentário em um projeto de suplemento do VSTO  
 Os exemplos a seguir pressupõem que há uma única célula <xref:Microsoft.Office.Interop.Excel.Range> chamado `dateComment` na planilha ativa.  
  
#### <a name="to-add-a-new-comment-to-an-excel-range"></a>Para adicionar um novo comentário a um intervalo do Excel  
  
1.  Chamar o <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> método o <xref:Microsoft.Office.Interop.Excel.Range> e forneça o texto do comentário.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#20](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#20)]  
  
#### <a name="to-delete-a-comment-from-an-excel-range"></a>Para excluir um comentário de um intervalo do Excel  
  
1.  Verifique se existe um comentário no intervalo e excluí-lo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#19](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#19)]  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com planilhas](../vsto/working-with-worksheets.md)   
 [Como: exibir programaticamente os comentários da planilha](../vsto/how-to-programmatically-display-worksheet-comments.md)   
 [Controle NamedRange](../vsto/namedrange-control.md)  
  
  