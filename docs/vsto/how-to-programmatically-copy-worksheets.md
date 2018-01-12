---
title: 'Como: copiar planilhas programaticamente | Microsoft Docs'
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
- worksheets, copying
- Excel [Office development in Visual Studio], copying worksheets
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: fe8b289dd30ea44331a2ae0c63dd451da8969369
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-copy-worksheets"></a>Como copiar planilhas programaticamente
  Você pode criar uma cópia de uma planilha e inserir essa planilha antes ou depois de uma planilha existente na pasta de trabalho. Se você não especificar onde inserir a planilha, o Excel cria uma nova pasta de trabalho para conter a nova planilha.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  Se você copiar a planilha programaticamente, ou o usuário final copia a planilha manualmente, não há nenhum código por trás da nova planilha e controles na nova planilha não funcionam. Isso ocorre porque a planilha copiada recentemente é um <xref:Microsoft.Office.Interop.Excel.Worksheet> objeto e não um <xref:Microsoft.Office.Tools.Excel.Worksheet> item de host. Controles de host e controles de formulários do Windows só podem ser adicionados aos itens de host. Para obter mais informações, consulte [limitações programáticas de itens de Host e controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>Para adicionar uma planilha copiada para uma pasta de trabalho em uma personalização no nível do documento  
  
1.  Use o <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> método para copiar a primeira planilha na pasta de trabalho atual e colocar a cópia após a terceira planilha.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#16)]  
  
### <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Para adicionar uma planilha copiada para uma pasta de trabalho em um suplemento do VSTO  
  
1.  Use o <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> método para copiar a primeira planilha na pasta de trabalho atual e colocar a cópia após a terceira planilha.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com planilhas](../vsto/working-with-worksheets.md)   
 [Itens de host e visão geral dos controles de Host](../vsto/host-items-and-host-controls-overview.md)   
 [Como: adicionar novas planilhas a pastas de trabalho programaticamente](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Como: excluir planilhas programaticamente de pastas de trabalho](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Como: Selecionar planilhas programaticamente](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automatizando o Excel usando objetos estendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Limitações programáticas de itens de Host e controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  