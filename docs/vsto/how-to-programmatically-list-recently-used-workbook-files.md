---
title: 'Como: programaticamente a lista de usados recentemente arquivos da pasta de trabalho | Microsoft Docs'
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
- workbooks, listing recently used
- RecentFiles property
- Excel [Office development in Visual Studio], recently used files listing
- recent file list, Excel
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e8a64f8a934e8cd7cdbbed11a87d15e795d19d0f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-list-recently-used-workbook-files"></a>Como listar programaticamente arquivos de pasta de trabalho usados recentemente
  O <xref:Microsoft.Office.Interop.Excel._Application.RecentFiles%2A> propriedade retorna uma coleção que contém os nomes de todos os arquivos que aparecem na lista do Microsoft Office Excel de arquivos usados recentemente. O comprimento da lista varia dependendo do número de arquivos que o usuário selecionou para manter. Você pode exibir os resultados em um intervalo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-list-recently-used-workbooks-in-a-range-object"></a>Para pastas de trabalho de lista usada recentemente em um objeto de intervalo  
  
1.  Percorra a lista de arquivos recentes e exibir os nomes de células relativo a um <xref:Microsoft.Office.Interop.Excel.Range> objeto.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com pastas de trabalho](../vsto/working-with-workbooks.md)   
 [Controle NamedRange](../vsto/namedrange-control.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  