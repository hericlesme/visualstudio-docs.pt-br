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
ms.assetid: 1e6131ad-0e5b-4189-be67-5b2ed87d193d
caps.latest.revision: "35"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 28468eaba28d36394754b96bdb13727088885ff1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
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
  
  