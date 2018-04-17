---
title: 'Como: aplicar cor a intervalos do Excel programaticamente | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- color, Excel ranges
- ranges, applying color
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b518cfb4f1ef7c5d757e4a68bbc12b51c6c61ae3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Como aplicar cor a intervalos do Excel programaticamente
  Para aplicar uma cor ao texto dentro de um intervalo de células, use um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle ou um objeto nativo de intervalo do Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>Usando um controle NamedRange  
 Este exemplo é para personalizações no nível do documento.  
  
#### <a name="to-apply-color-to-a-namedrange-control"></a>Para aplicar cor a um controle NamedRange  
  
1.  Criar um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle na célula A1.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#65)]  
  
2.  Definir a cor do texto no <xref:Microsoft.Office.Tools.Excel.NamedRange> controle.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#66)]  
  
## <a name="using-native-excel-ranges"></a>Usando intervalos do Excel nativo  
  
#### <a name="to-apply-color-to-a-native-excel-range-object"></a>Para aplicar cor a um objeto nativo de intervalo do Excel  
  
1.  Criar um intervalo na célula A1 e, em seguida, definir a cor do texto.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#67)]  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com intervalos](../vsto/working-with-ranges.md)   
 [Controle NamedRange](../vsto/namedrange-control.md)   
 [Como: aplicar estilos a intervalos em pastas de trabalho programaticamente](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Como: referência a intervalos de planilhas em código programaticamente](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Automatizando o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  