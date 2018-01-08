---
title: 'Como: copiar programaticamente os dados e formatar em planilhas | Microsoft Docs'
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
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
ms.assetid: eed7dbaf-bdb5-4330-ba2e-5f3d50817eca
caps.latest.revision: "37"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9f8b976427abe35ef8383604eea93f1513316903
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Como copiar dados e formatar em planilhas programaticamente
  Você pode copiar dados de um intervalo em uma planilha para todas as outras planilhas em uma pasta de trabalho usando o <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> método. Especifique um intervalo, e se você deseja copiar dados, formatação ou ambos.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer um intervalo nomeado `rangeData` em uma planilha.  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com planilhas](../vsto/working-with-worksheets.md)   
 [Como: adicionar novas planilhas a pastas de trabalho programaticamente](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Como: alterar programaticamente a formatação em linhas da planilha que contém as células selecionadas](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  