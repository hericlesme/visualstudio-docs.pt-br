---
title: 'Como: remover proteção de planilhas programaticamente | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, unprotecting
- documents [Office development in Visual Studio], document protection
- document protection, removing from worksheets
- Unprotect method
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c9e34e184462f1ec7822b5c2fce63aaff4a7f515
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Como remover proteção de planilhas programaticamente
  Programaticamente, você pode remover proteção de uma planilha do Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 O exemplo a seguir usa a variável `getPasswordFromUser`, que contém uma senha obtida do usuário.  
  
### <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>Para desproteger uma planilha em uma personalização no nível do documento  
  
1.  Chamar o <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> método da planilha e passe a senha, se necessário. Este exemplo presume que você está trabalhando com uma planilha denominada `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#28)]  
  
### <a name="to-unprotect-a-worksheet-in-an-vsto-add-in"></a>Para desproteger uma planilha em um suplemento do VSTO  
  
1.  Chamar o <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> método da planilha ativa e passe a senha, se necessário.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#18)]  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com planilhas](../vsto/working-with-worksheets.md)   
 [Como: proteger planilhas programaticamente](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Como: programaticamente proteger pastas de trabalho](../vsto/how-to-programmatically-protect-workbooks.md)   
 [Como: ocultar planilhas programaticamente](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  