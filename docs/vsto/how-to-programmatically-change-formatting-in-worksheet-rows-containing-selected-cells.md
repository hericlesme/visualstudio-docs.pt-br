---
title: "Como: alterar programaticamente a formatação em linhas da planilha que contém as células selecionadas | Microsoft Docs"
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
- rows [Office development in Visual Studio]
- formatting [Office development in Visual Studio]
- worksheets, changing formatting
ms.assetid: c55cd488-98d1-46c6-9715-0e9212d178de
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2763571f7854653707116d233628e6bff539827f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells"></a>Como alterar a formatação em linhas de planilhas que contêm células selecionadas programaticamente
  Você pode alterar a fonte de uma linha inteira que contém uma célula selecionada para que o texto está em negrito.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-make-the-current-row-bold-and-the-previously-bolded-row-normal"></a>Para tornar a linha atual em negrito e o anteriormente em negrito linha normal  
  
1.  Declare uma variável estática para controlar a linha selecionada anteriormente.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#37](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#37)]
     [!code-vb[Trin_VstcoreExcelAutomation#37](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#37)]  
  
2.  Recuperar uma referência para a célula atual usando o <xref:Microsoft.Office.Interop.Excel._Application.ActiveCell%2A> propriedade.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#38)]
     [!code-vb[Trin_VstcoreExcelAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#38)]  
  
3.  Estilo de atual de linha em negrito usando o <xref:Microsoft.Office.Interop.Excel.Range.EntireRow%2A> propriedade da célula ativa.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#39)]
     [!code-vb[Trin_VstcoreExcelAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#39)]  
  
4.  Certifique-se de que o valor atual de `previousRow` é não em 0. 0 (zero) indica que essa é a primeira vez que esse código.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#40)]
     [!code-vb[Trin_VstcoreExcelAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#40)]  
  
5.  Certifique-se de que a linha atual é diferente da linha anterior.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#41)]
     [!code-vb[Trin_VstcoreExcelAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#41)]  
  
6.  Recuperar uma referência a um intervalo que representa a linha que foi previamente selecionada e conjunto que não seja de linha em negrito.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#42](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#42)]
     [!code-vb[Trin_VstcoreExcelAutomation#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#42)]  
  
7.  Armazene a linha atual para que ele pode se tornar a linha anterior no próximo passo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#43](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#43)]
     [!code-vb[Trin_VstcoreExcelAutomation#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#43)]  
  
 O exemplo a seguir mostra o método complete.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[Trin_VstcoreExcelAutomation#36](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#36)]
 [!code-vb[Trin_VstcoreExcelAutomation#36](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#36)]  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com planilhas](../vsto/working-with-worksheets.md)   
 [Como: aplicar estilos a intervalos em pastas de trabalho programaticamente](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Como: copiar programaticamente os dados e formatar em planilhas](../vsto/how-to-programmatically-copy-data-and-formatting-across-worksheets.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  