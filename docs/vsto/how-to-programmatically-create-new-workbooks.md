---
title: 'Como: criar programaticamente novas pastas de trabalho | Microsoft Docs'
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
- Excel [Office development in Visual Studio], creating workbooks
- workbooks, creating
ms.assetid: be0196fe-7dc5-4811-b0cd-3c219731a3ff
caps.latest.revision: "48"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 59578b57bcff053558eba522e88c2e246fc45942
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-create-new-workbooks"></a>Como criar novas pastas de trabalho programaticamente
  Quando você cria uma pasta de trabalho por meio de programação, é um nativo <xref:Microsoft.Office.Interop.Excel.Workbook> do objeto, não um <xref:Microsoft.Office.Tools.Excel.Workbook> item de host.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Você pode gerar um <xref:Microsoft.Office.Tools.Excel.Workbook> item de host para um <xref:Microsoft.Office.Interop.Excel.Workbook> objeto no projeto de suplemento do VSTO. Para obter mais informações, consulte [Estendendo documentos do Word e pastas de trabalho do Excel no suplemento do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
### <a name="to-create-a-new-workbook"></a>Para criar uma nova pasta de trabalho  
  
1.  Use o <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> método o <xref:Microsoft.Office.Interop.Excel.Workbooks> coleção.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#1)]  
  
    > [!NOTE]  
    >  Você pode criar uma pasta de trabalho com base em um modelo que não seja o modelo padrão: passar o modelo que você deseja usar como um parâmetro para o <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> método.  
  
## <a name="see-also"></a>Consulte também  
 [Estendendo documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Adicionando controles a documentos do Office em tempo de execução](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Trabalhando com pastas de trabalho](../vsto/working-with-workbooks.md)   
 [Como: programaticamente abrir pastas de trabalho](../vsto/how-to-programmatically-open-workbooks.md)   
 [Como: programaticamente salvar pastas de trabalho](../vsto/how-to-programmatically-save-workbooks.md)   
 [Como: programaticamente fechar pastas de trabalho](../vsto/how-to-programmatically-close-workbooks.md)   
 [Limitações programáticas de itens de Host e controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Visão geral dos Controles de Host e dos Itens de Host](../vsto/host-items-and-host-controls-overview.md)  
  
  