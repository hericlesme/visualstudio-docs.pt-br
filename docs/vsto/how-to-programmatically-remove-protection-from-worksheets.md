---
title: "Como: remover proteção de planilhas programaticamente | Microsoft Docs"
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
- worksheets, unprotecting
- documents [Office development in Visual Studio], document protection
- document protection, removing from worksheets
- Unprotect method
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1b4564baab3cf2daa6e8859a66dbc6e9e06ffdef
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
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
  
  