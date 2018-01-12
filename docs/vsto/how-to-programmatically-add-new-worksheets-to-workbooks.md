---
title: 'Como: adicionar novas planilhas a pastas de trabalho programaticamente | Microsoft Docs'
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
- workbooks, adding worksheets
- workbooks, creating worksheets
- worksheets, creating
- worksheets, adding to workbooks
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 239d4cdba093fa81eea75e1a74906b184e6ba855
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>Como adicionar novas planilhas a pastas de trabalho programaticamente
  Você pode criar programaticamente uma planilha e, em seguida, adicionar a planilha para a coleção de planilhas na pasta de trabalho.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-add-a-new-worksheet-to-a-workbook-in-a-document-level-customization"></a>Para adicionar uma nova planilha para uma pasta de trabalho em uma personalização no nível do documento  
  
1.  Use o <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> método o <xref:Microsoft.Office.Interop.Excel.Sheets> coleção.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#15)]  
  
     A nova planilha é um nativo <xref:Microsoft.Office.Interop.Excel.Worksheet> objeto e não um item de host. Se você deseja adicionar um <xref:Microsoft.Office.Tools.Excel.Worksheet> item de host, você deve adicionar a planilha em tempo de design.  
  
### <a name="to-add-a-new-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Para adicionar uma nova planilha para uma pasta de trabalho em um suplemento do VSTO  
  
1.  Use o <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> método o <xref:Microsoft.Office.Interop.Excel.Sheets> coleção.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#11)]  
  
     A nova planilha é um nativo <xref:Microsoft.Office.Interop.Excel.Worksheet> objeto e não um item de host. Você também pode gerar um <xref:Microsoft.Office.Tools.Excel.Worksheet> item de host do nativo <xref:Microsoft.Office.Interop.Excel.Worksheet> objeto. Para obter mais informações, consulte [Estendendo documentos do Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com planilhas](../vsto/working-with-worksheets.md)   
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Como: excluir planilhas programaticamente de pastas de trabalho](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Como: Selecionar planilhas programaticamente](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automatizando o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  