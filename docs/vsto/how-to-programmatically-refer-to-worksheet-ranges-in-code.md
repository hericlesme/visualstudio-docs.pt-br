---
title: "Como: referência a intervalos de planilhas em código programaticamente | Microsoft Docs"
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
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 001efb4609059ba68a0a6a5f9c30d2f416805013
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Como fazer referência a intervalos de planilhas em código programaticamente
  Usar um processo semelhante para fazer referência ao conteúdo de um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle ou um objeto nativo de intervalo do Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>Usando um controle NamedRange  
 O exemplo a seguir adiciona um <xref:Microsoft.Office.Tools.Excel.NamedRange> em uma planilha e, em seguida, adiciona o texto para a célula no intervalo.  
  
#### <a name="to-refer-to-a-namedrange-control"></a>Para se referir a um controle NamedRange  
  
1.  Atribuir uma cadeia de caracteres para o <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> propriedade o <xref:Microsoft.Office.Tools.Excel.NamedRange> controle. Esse código deve ser colocado em uma classe de folha, não o `ThisWorkbook` classe.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]  
  
## <a name="using-native-excel-ranges"></a>Usando intervalos do Excel nativo  
 O exemplo a seguir adiciona um intervalo do Excel nativo em uma planilha e, em seguida, adiciona o texto para a célula no intervalo.  
  
#### <a name="to-refer-to-a-native-range-object"></a>Para fazer referência a um objeto range nativo  
  
1.  Atribuir uma cadeia de caracteres para o <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> propriedade do intervalo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com intervalos](../vsto/working-with-ranges.md)   
 [Como: verificar a ortografia em planilhas programaticamente](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Como: aplicar estilos a intervalos em pastas de trabalho programaticamente](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Como: preencher intervalos programaticamente automaticamente com dados de alteração incremental](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Como: pesquisar texto em intervalos de planilhas programaticamente](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [Controle NamedRange](../vsto/namedrange-control.md)   
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitações programáticas de itens de Host e controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  