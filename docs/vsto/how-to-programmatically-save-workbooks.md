---
title: 'Como: programaticamente salvar pastas de trabalho | Microsoft Docs'
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
- workbooks, saving in XML format
- workbooks, saving
- workbooks, saving backup copies
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4d184d7122459b85b3ad20fbf8338a53f28bd6c8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-save-workbooks"></a>Como salvar pastas de trabalho programaticamente
  Há várias maneiras de salvar uma pasta de trabalho. Você pode salvar uma pasta de trabalho sem alterar o caminho. Se a pasta de trabalho não tiver sido salvo antes, você deve salvar a pasta de trabalho, especificando um caminho. Sem um caminho explícito, o Microsoft Office Excel salva o arquivo na pasta atual com o nome que foi fornecido quando ele foi criado. Você também pode salvar uma cópia da pasta de trabalho sem modificar a pasta de trabalho aberta na memória.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="saving-a-workbook-without-changing-the-path"></a>Salvar uma pasta de trabalho sem alterar o caminho  
  
#### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Para salvar uma pasta de trabalho associada a uma personalização no nível do documento  
  
1.  Chamar o <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> método da classe ThisWorkbook.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#4)]  
  
#### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Para salvar a pasta de trabalho ativa em um suplemento do VSTO  
  
1.  Chamar o <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> método para salvar a pasta de trabalho ativa. Para usar o exemplo de código a seguir, executá-lo no `ThisAddIn` classe em um projeto de suplemento do VSTO para Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="saving-a-workbook-with-a-new-path"></a>Salvar uma pasta de trabalho com um novo caminho  
 Você pode salvar a pasta de trabalho especificada para um novo local ou com um novo nome, opcionalmente, especificar um formato de arquivo, uma senha, um modo de acesso e muito mais.  
  
> [!NOTE]  
>  Talvez você queira definir o <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> propriedade **False** antes de salvar a pasta de trabalho com um novo caminho como salvando em alguns formatos requer interação. Definir essa propriedade como **False** faz com que o Excel para usar todos os padrões.  
  
#### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Para salvar uma pasta de trabalho associada a uma personalização no nível do documento  
  
1.  Chamar o <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> método o `ThisWorkbook` classe. Para usar o exemplo de código a seguir, executá-lo no `ThisWorkbook` classe.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#5)]  
  
#### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Para salvar a pasta de trabalho ativa em um suplemento do VSTO  
  
1.  Chamar o <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> método para salvar um novo caminho de pasta de trabalho ativa. Para usar o exemplo de código a seguir, executá-lo no `ThisAddIn` classe em um projeto de suplemento do VSTO para Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="saving-a-copy-of-the-workbook"></a>Salvar uma cópia da pasta de trabalho  
 Você pode salvar uma cópia da pasta de trabalho em um arquivo sem modificar a pasta de trabalho aberta na memória. Isso é útil quando você deseja criar uma cópia de backup sem modificar o local da pasta de trabalho.  
  
#### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Para salvar uma pasta de trabalho associada a uma personalização no nível do documento  
  
1.  Chamar o <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> método o `ThisWorkbook` classe. Para usar o exemplo de código a seguir, executá-lo no `ThisWorkbook` classe.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#6)]  
  
#### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Para salvar a pasta de trabalho ativa em um suplemento do VSTO  
  
1.  Chamar o <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> método para salvar uma cópia da pasta de trabalho ativa. Para usar o exemplo de código a seguir, executá-lo no `ThisAddIn` classe em um projeto de suplemento do VSTO para Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="robust-programming"></a>Programação robusta  
 Cancelar interativamente a qualquer um dos métodos que salvar ou copiar a pasta de trabalho gera um erro de tempo de execução em seu código. Por exemplo, se o procedimento chama o <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> método mas não desative prompts do Excel, e a usuário clica em **Cancelar** quando solicitado, o Excel gera um erro de tempo de execução.  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com pastas de trabalho](../vsto/working-with-workbooks.md)   
 [Item de Host de pasta de trabalho](../vsto/workbook-host-item.md)   
 [Como: programaticamente fechar pastas de trabalho](../vsto/how-to-programmatically-close-workbooks.md)   
 [Limitações programáticas de itens de Host e controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Visão geral dos Controles de Host e dos Itens de Host](../vsto/host-items-and-host-controls-overview.md)  
  
  