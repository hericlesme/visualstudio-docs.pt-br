---
title: "Como: programaticamente restaurar seleções após pesquisas | Microsoft Docs"
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
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: adbc31968b74dd6cb47f06e6feb2cd7d2848f7e7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>Como restaurar seleções após pesquisas programaticamente
  Se você localizar e substituir texto em um documento, você talvez queira restaurar a seleção do usuário original depois que a pesquisa é concluída.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 O código no procedimento de exemplo usa dois <xref:Microsoft.Office.Interop.Word.Range> objetos. Um armazena o valor atual <xref:Microsoft.Office.Interop.Word.Selection>, e define o documento inteiro a ser usado como um intervalo de pesquisa.  
  
### <a name="to-restore-the-users-original-selection-after-a-search"></a>Para restaurar a seleção do usuário original após uma pesquisa  
  
1.  Criar o <xref:Microsoft.Office.Interop.Word.Range> objetos para o documento e a seleção atual.  
  
     [!code-vb[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#83)]
     [!code-csharp[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#83)]  
  
2.  Executar a pesquisa e a operação de substituição.  
  
     [!code-vb[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#84)]
     [!code-csharp[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#84)]  
  
3.  Selecione o intervalo de início para restaurar a seleção do usuário original.  
  
     [!code-vb[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#85)]
     [!code-csharp[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#85)]  
  
 O exemplo a seguir mostra o método complete.  
  
## <a name="example"></a>Exemplo  
 [!code-vb[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#82)]
 [!code-csharp[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#82)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: programaticamente pesquisar e substituir texto em documentos](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Como: definir opções de pesquisa no Word](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Como: programaticamente percorrer itens encontrados em documentos](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  