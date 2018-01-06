---
title: 'Como: programaticamente fechar pastas de trabalho | Microsoft Docs'
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
- workbooks, closing
- Excel [Office development in Visual Studio], closing workbooks
ms.assetid: 50709caf-2ad8-4843-987c-9a34c8c1e4fe
caps.latest.revision: "52"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1cb28dc5b9df265178f26a0573ffe3eb5f5043d5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-close-workbooks"></a>Como fechar pastas de trabalho programaticamente
  Você pode fechar a pasta de trabalho ativa, ou você pode especificar uma pasta de trabalho para fechar.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="closing-the-active-workbook"></a>Fechar a pasta de trabalho ativa  
 Há dois procedimentos para fechar a pasta de trabalho ativa: uma para personalizações no nível do documento e uma para suplementos do VSTO.  
  
#### <a name="to-close-the-active-workbook-in-a-document-level-customization"></a>Para fechar a pasta de trabalho ativa uma personalização de nível de documento  
  
1.  Chamar o <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> método para fechar a pasta de trabalho associada com a personalização. Para usar o exemplo de código a seguir, executá-lo no `Sheet1` classe em um projeto de nível de documento para Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#3)]  
  
#### <a name="to-close-the-active-workbook-in-a-vsto-add-in"></a>Para fechar a pasta de trabalho ativa em um suplemento do VSTO  
  
1.  Chamar o <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> método para fechar a pasta de trabalho ativa. Para usar o exemplo de código a seguir, executá-lo no `ThisAddIn` classe em um projeto de suplemento do VSTO para Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="closing-a-workbook-that-you-specify-by-name"></a>Fechar uma pasta de trabalho que você especifica por nome  
 A maneira que você fechar uma pasta de trabalho que você especifica por nome é o mesmo para suplementos do VSTO e personalizações no nível do documento.  
  
#### <a name="to-close-a-workbook-that-you-specify-by-name"></a>Para fechar uma pasta de trabalho que você especifica por nome  
  
1.  Especifique o nome de pasta de trabalho como um argumento para o <xref:Microsoft.Office.Interop.Excel.Workbooks> coleção. O exemplo de código a seguir pressupõe que uma pasta de trabalho denominada **NewWorkbook** é aberto no Excel.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com pastas de trabalho](../vsto/working-with-workbooks.md)   
 [Como: programaticamente salvar pastas de trabalho](../vsto/how-to-programmatically-save-workbooks.md)   
 [Como: programaticamente abrir pastas de trabalho](../vsto/how-to-programmatically-open-workbooks.md)   
 [Limitações programáticas de itens de Host e controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Visão geral dos Controles de Host e dos Itens de Host](../vsto/host-items-and-host-controls-overview.md)  
  
  