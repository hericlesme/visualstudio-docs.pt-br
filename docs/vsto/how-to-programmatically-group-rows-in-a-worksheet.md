---
title: 'Como: programaticamente agrupar linhas em uma planilha | Microsoft Docs'
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
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
ms.assetid: 48037dca-35a2-4df2-918b-6a9f568fae91
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c11911d6d9e7b92b7a86b21723c8788afe15a57b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Como agrupar linhas em uma planilha programaticamente
  Você pode agrupar uma ou mais linhas inteiras. Para criar um grupo em uma planilha, use um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle ou um objeto nativo de intervalo do Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>Usando um controle NamedRange  
 Se você adicionar um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle a um projeto de nível de documento em tempo de design, você pode usar o controle para criar programaticamente um grupo. O exemplo a seguir assume que há três <xref:Microsoft.Office.Tools.Excel.NamedRange> controles na mesma planilha: `data2001`, `data2002`, e `dataAll`. Cada intervalo nomeado refere-se a uma linha inteira na planilha.  
  
#### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>Para criar um grupo de controles NamedRange em uma planilha  
  
1.  Grupo de três intervalos nomeados chamando o <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> método de cada intervalo. Esse código deve ser colocado em uma classe de folha, não o `ThisWorkbook` classe.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]  
  
    > [!NOTE]  
    >  Para desagrupar linhas, chame o <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> método.  
  
## <a name="using-native-excel-ranges"></a>Usando intervalos do Excel nativo  
 O código presume que você tenha três intervalos do Excel denominados `data2001`, `data2002`, e `dataAll` em uma planilha.  
  
#### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>Para criar um grupo de intervalos do Excel em uma planilha  
  
1.  Grupo de três intervalos nomeados chamando o <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> método de cada intervalo. O exemplo a seguir assume que há três <xref:Microsoft.Office.Interop.Excel.Range> controles denominados `data2001`, `data2002`, e `dataAll` na mesma planilha. Cada intervalo nomeado refere-se a uma linha inteira na planilha.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]  
  
    > [!NOTE]  
    >  Para desagrupar linhas, chame o <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> método.  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com planilhas](../vsto/working-with-worksheets.md)   
 [Controle NamedRange](../vsto/namedrange-control.md)   
 [Como: adicionar controles NamedRange a planilhas](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  