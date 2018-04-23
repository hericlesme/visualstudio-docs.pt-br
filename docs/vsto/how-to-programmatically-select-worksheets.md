---
title: 'Como: Selecionar planilhas programaticamente | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5d0862f83d77365e07df1e61b7063a9e5ecd4f37
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-select-worksheets"></a>Como selecionar planilhas programaticamente
  O <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> método seleciona o objeto especificado, que move a seleção do usuário para o novo objeto. Use o <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> método se você deseja colocar o foco para o objeto sem alterar a seleção do usuário.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Se você deseja selecionar uma planilha existente em um suplemento do VSTO ou se a planilha foi criada em tempo de execução em uma personalização no nível do documento, você deverá acessá-lo usando o Excel <xref:Microsoft.Office.Interop.Excel.Sheets> coleção da pasta de trabalho do Excel; caso contrário, você pode acessar o <xref:Microsoft.Office.Tools.Excel.Worksheet>diretamente o item de host.  
  
## <a name="using-the-worksheet-host-item"></a>Usando o Item de Host de planilha  
 Uma personalização de nível de documento, adicione o seguinte código para **Sheet1.vb** ou **Sheet1.cs**.  
  
#### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Para selecionar a primeira planilha em uma pasta de trabalho usando um item de host  
  
1.  Chame o método <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> de `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]  
  
## <a name="using-the-sheets-collection-of-the-excel-workbook"></a>Usando a coleção de folhas da pasta de trabalho do Excel  
 Acessar a planilha usando o Excel <xref:Microsoft.Office.Interop.Excel.Sheets> coleção.  
  
#### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Para selecionar a primeira planilha em uma pasta de trabalho usando a coleção de folhas da pasta de trabalho do Excel  
  
1.  Chamar o <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> método o <xref:Microsoft.Office.Interop.Excel.Sheets> coleção para selecionar a primeira planilha da pasta de trabalho ativa.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com planilhas](../vsto/working-with-worksheets.md)   
 [Como: Imprimir planilhas programaticamente](../vsto/how-to-programmatically-print-worksheets.md)   
 [Como: excluir planilhas programaticamente de pastas de trabalho](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Como: ocultar planilhas programaticamente](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Como: proteger planilhas programaticamente](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Item de Host de planilha](../vsto/worksheet-host-item.md)   
 [Acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Limitações programáticas de itens de Host e controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Visão geral dos Controles de Host e dos Itens de Host](../vsto/host-items-and-host-controls-overview.md)  
  
  