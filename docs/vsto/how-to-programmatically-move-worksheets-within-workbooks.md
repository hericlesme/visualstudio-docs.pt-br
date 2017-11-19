---
title: 'Como: programaticamente mover planilhas em pastas de trabalho | Microsoft Docs'
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
- worksheets, moving
- workbooks, moving worksheets in
ms.assetid: a010a633-412e-4299-9587-cacb035842c1
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 12597413fccfc9b7b43b322085e36148981be9db
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>Como mover planilhas em pastas de trabalho programaticamente
  Programaticamente, você pode alterar a posição de planilhas em relação a outras planilhas em uma pasta de trabalho. Se você não especificar um local para a planilha movida, o Excel cria uma nova pasta de trabalho para contê-lo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-move-a-worksheet-in-a-document-level-customization"></a>Para mover uma planilha em uma personalização no nível do documento  
  
1.  Atribuir o número total de planilhas na pasta de trabalho a uma variável e, em seguida, mova a primeira planilha para que ele se torna o último deles.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#24)]  
  
### <a name="to-move-a-worksheet-in-an-vsto-add-in"></a>Para mover uma planilha em um suplemento do VSTO  
  
1.  Atribuir o número total de planilhas na pasta de trabalho a uma variável e, em seguida, mova a primeira planilha para que ele se torna o último deles.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#16)]  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com planilhas](../vsto/working-with-worksheets.md)   
 [Como: ocultar planilhas programaticamente](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Como: excluir planilhas programaticamente de pastas de trabalho](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Como: proteger planilhas programaticamente](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  