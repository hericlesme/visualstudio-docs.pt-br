---
title: "Como: exibir uma cadeia de caracteres em uma célula de planilha programaticamente | Microsoft Docs"
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
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4a76d2588ec07c461794381a2edd502d367be274
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Como exibir uma cadeia de caracteres em uma célula de planilha programaticamente
  Este exemplo demonstra como exibir o texto em uma célula por meio de programação. Para exibir o texto na célula, use um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle ou um objeto nativo de intervalo do Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>Usando um controle NamedRange  
 Este exemplo usa um <xref:Microsoft.Office.Tools.Excel.NamedRange> controle chamado `message`. O controle deve ser adicionado a uma personalização no nível do documento em tempo de design. O código a seguir deve ser colocado em uma classe de folha, não o `ThisWorkbook` classe.  
  
#### <a name="to-display-text-in-a-namedrange-control"></a>Para exibir o texto em um controle NamedRange  
  
1.  Defina o valor da <xref:Microsoft.Office.Tools.Excel.NamedRange> controle **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]  
  
## <a name="using-a-native-excel-range"></a>Usando um intervalo do Excel nativo  
 O código a seguir cria um novo intervalo de forma programática e, em seguida, atribui um valor a ela.  
  
#### <a name="to-display-text-in-an-excel-range"></a>Para exibir texto em um intervalo do Excel  
  
1.  Recuperar o intervalo na célula **A1** na `Sheet1` e defina o valor como **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Coletando dados usando um formulário do Windows](../vsto/walkthrough-collecting-data-using-a-windows-form.md)   
 [Solucionando problemas de soluções do Office](../vsto/troubleshooting-office-solutions.md)   
 [Controle NamedRange](../vsto/namedrange-control.md)   
 [Acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  