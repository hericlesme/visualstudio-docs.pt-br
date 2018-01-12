---
title: 'Como: programaticamente armazenar e recuperar valores de data em intervalos do Excel | Microsoft Docs'
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
- Excel [Office development in Visual Studio], retrieving date values from ranges
- ranges, retrieving data values
- dates, retrieving from Excel ranges
- Excel [Office development in Visual Studio], storing date values in ranges
- date values, storing in Excel ranges
- dates, storing in Excel ranges
- ranges, storing date values
- date values
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 589079a593400549a69940fc42d1cf25fcab8826
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Como armazenar e recuperar valores de datas em intervalos do Excel programaticamente
  Você pode armazenar e recuperar valores em um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle ou um objeto nativo de intervalo do Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Se você armazenar um valor de data que está em ou após 1/1/1900 em um intervalo usando ferramentas de desenvolvimento do Office no Visual Studio, ele é armazenado no formato OLE Automation (OA). Você deve usar o <xref:System.DateTime.FromOADate%2A> método para recuperar o valor de datas de OLE Automation (OA). Se a data for anterior a 1/1/1900, ela será armazenada como uma cadeia de caracteres.  
  
> [!NOTE]  
>  Datas do Excel são diferentes das datas de automação OLE para os primeiros dois meses de 1900. Também há diferenças se o **sistema de data de 1904** opção estiver marcada. Os exemplos de código a seguir não abordam essas diferenças.  
  
## <a name="using-a-namedrange-control"></a>Usando um controle NamedRange  
  
-   Este exemplo é para personalizações no nível do documento. O código a seguir deve ser colocado em uma classe de folha, não o `ThisWorkbook` classe.  
  
#### <a name="to-store-a-date-value-in-a-named-range"></a>Para armazenar um valor de data em um intervalo nomeado  
  
1.  Criar um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle na célula **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]  
  
2.  Definir a data de hoje como o valor para `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]  
  
#### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Para recuperar um valor de data de um intervalo nomeado  
  
1.  Recuperar o valor de data de `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]  
  
## <a name="using-native-excel-ranges"></a>Usando intervalos do Excel nativo  
  
#### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Para armazenar um valor de data em um objeto nativo de intervalo do Excel  
  
1.  Criar um <xref:Microsoft.Office.Interop.Excel.Range> que representa a célula **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]  
  
2.  Definir a data de hoje como o valor para `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]  
  
#### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Para recuperar um valor de data de um objeto nativo de intervalo do Excel  
  
1.  Recuperar o valor de data de `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com intervalos](../vsto/working-with-ranges.md)   
 [Visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md)   
 [Controle NamedRange](../vsto/namedrange-control.md)   
 [Como: referência a intervalos de planilhas em código programaticamente](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Como: adicionar controles NamedRange a planilhas](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  