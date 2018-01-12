---
title: "Como: preencher intervalos programaticamente automaticamente com a alteração de dados incrementalmente | Microsoft Docs"
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
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: d6634fea629358368d3b61c5b505e5eec7ec0186
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Como preencher intervalos automaticamente com dados alterados em incrementos programaticamente
  O <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> método o <xref:Microsoft.Office.Interop.Excel.Range> objeto permite que você preencha um intervalo em uma planilha com valores automaticamente. Geralmente, o <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> método é usado para armazenar incrementalmente aumentando ou diminuindo a valores em um intervalo. Você pode especificar o comportamento, fornecendo uma constante opcional do <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> enumeração.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Você deve especificar dois intervalos ao usar <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>:  
  
-   O intervalo que chama o <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> método, que especifica o ponto de partida do preenchimento e contém um valor inicial.  
  
-   O intervalo que você deseja preencher, passado como um parâmetro para o <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> método. Este intervalo de destino deve incluir o intervalo que contém o valor inicial.  
  
    > [!NOTE]  
    >  Você não pode passar um <xref:Microsoft.Office.Tools.Excel.NamedRange> controlar em vez do <xref:Microsoft.Office.Interop.Excel.Range>. Para obter mais informações, consulte [limitações programáticas de itens de Host e controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 A primeira célula do intervalo que você deseja preencher deve conter um valor inicial.  
  
 O exemplo requer que você preenche três regiões:  
  
-   Coluna B é incluir cinco dias da semana. Para o valor inicial, digite **segunda** na célula B1.  
  
-   A coluna C é incluem a cinco meses. Para o valor inicial, digite **janeiro** na célula C1.  
  
-   A coluna D é incluir uma série de números, incrementando em dois para cada linha. Para obter os valores inicias, digite **4** na célula D1 e **6** na célula D2.  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com intervalos](../vsto/working-with-ranges.md)   
 [Como: referência a intervalos de planilhas em código programaticamente](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Como: aplicar estilos a intervalos em pastas de trabalho programaticamente](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Como: executar cálculos do Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  