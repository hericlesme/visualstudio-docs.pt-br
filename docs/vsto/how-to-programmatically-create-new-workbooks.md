---
title: 'Como: criar programaticamente novas pastas de trabalho | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], creating workbooks
- workbooks, creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0ba2054258beb762a6b554a49b7a64a77f83dd7a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
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
  
  