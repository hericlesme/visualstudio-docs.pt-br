---
title: 'Como: programaticamente abrir pastas de trabalho | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a243e4972bcee77aa9d76957ab5cce289e30e120
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-open-workbooks"></a>Como abrir pastas de trabalho programaticamente
  O <xref:Microsoft.Office.Interop.Excel.Workbooks> coleção no Microsoft Office Excel torna possível para trabalhar com todas as pastas de trabalho e abrir pastas de trabalho.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-open-an-existing-workbook"></a>Para abrir uma pasta de trabalho existente  
  
1.  Use o <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> método o <xref:Microsoft.Office.Interop.Excel.Workbooks> coleção, passando o caminho para a pasta de trabalho.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo de código requer o seguinte:  
  
-   Uma pasta de trabalho chamada `YourWorkbook.xls` deve existir em um diretório chamado `Test` na unidade C.  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com pastas de trabalho](../vsto/working-with-workbooks.md)   
 [Como: abrir programaticamente os arquivos de texto como pastas de trabalho](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)   
 [Como: criar programaticamente novas pastas de trabalho](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Como: programaticamente salvar pastas de trabalho](../vsto/how-to-programmatically-save-workbooks.md)   
 [Como: programaticamente fechar pastas de trabalho](../vsto/how-to-programmatically-close-workbooks.md)   
 [Limitações programáticas de itens de Host e controles de Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Visão geral dos Controles de Host e dos Itens de Host](../vsto/host-items-and-host-controls-overview.md)  
  
  