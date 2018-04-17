---
title: 'Como: programaticamente proteger pastas de trabalho | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, passwords
- documents [Office development in Visual Studio], document protection
- workbooks, unprotecting
- document protection, removing from workbooks
- document protection, adding to workbooks
- workbooks, protecting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 03cab4591bbca62c237877e39dabf40328768ccf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-protect-workbooks"></a>Como proteger pastas de trabalho programaticamente
  Você pode proteger uma pasta de trabalho do Excel do Microsoft Office para que os usuários não podem adicionar ou excluir planilhas e também desproteger a pasta de trabalho programaticamente. Opcionalmente, você pode especificar uma senha, indique se você deseja que a estrutura protegida (para que os usuários não é possível mover planilhas) e indique se deseja que o windows da pasta de trabalho protegidas.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Proteger uma pasta de trabalho não impedir que os usuários editem as células. Para proteger os dados, você deve proteger as planilhas. Para obter mais informações, consulte [como: proteger planilhas programaticamente](../vsto/how-to-programmatically-protect-worksheets.md).  
  
 Os exemplos de código a seguir usam uma variável para conter uma senha que é obtida do usuário.  
  
## <a name="protecting-a-workbook-that-is-part-of-a-document-level-customization"></a>Protegendo uma pasta de trabalho que faz parte de uma personalização no nível do documento  
  
#### <a name="to-protect-a-workbook"></a>Para proteger uma pasta de trabalho  
  
1.  Chamar o <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> método da pasta de trabalho e incluir uma senha. Para usar o exemplo de código a seguir, executá-lo no `ThisWorkbook` classe, não em uma classe de folha.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#10)]  
  
#### <a name="to-unprotect-a-workbook"></a>Para desproteger uma pasta de trabalho  
  
1.  Chamar o <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> método, passando uma senha, se necessário. Para usar o exemplo de código a seguir, executá-lo no `ThisWorkbook` classe, não em uma classe de folha.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#11)]  
  
## <a name="protecting-a-workbook-by-using-an-application-level-add-in"></a>Protegendo uma pasta de trabalho usando um suplemento no nível do aplicativo  
  
#### <a name="to-protect-a-workbook"></a>Para proteger uma pasta de trabalho  
  
1.  Chamar o <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> método da pasta de trabalho e incluir uma senha. Este exemplo de código usa a pasta de trabalho ativa. Para usar este exemplo, execute o código do `ThisAddIn` classe em seu projeto.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#6)]  
  
#### <a name="to-unprotect-a-workbook"></a>Para desproteger uma pasta de trabalho  
  
1.  Chamar o <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> método da pasta de trabalho ativa, passando uma senha, se necessário. Para usar este exemplo, execute o código do `ThisAddIn` classe em seu projeto.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com pastas de trabalho](../vsto/working-with-workbooks.md)   
 [Como: proteger planilhas programaticamente](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Como: ocultar planilhas programaticamente](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  