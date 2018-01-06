---
title: "Como: definir opções de pesquisa no Word | Microsoft Docs"
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
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
ms.assetid: 4412b4e8-2868-4afb-a593-983603ef9b02
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b6bd57dfbb7cec6075d72b80228e77669e365dd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Como definir opções de pesquisa no Word programaticamente
  Há duas maneiras de definir opções de pesquisa para seleções em documentos do Microsoft Office Word:  
  
-   Definir as propriedades individuais de um <xref:Microsoft.Office.Interop.Word.Find> objeto.  
  
-   Usar argumentos a <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método de um <xref:Microsoft.Office.Interop.Word.Find> objeto.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="using-properties-of-a-find-object"></a>Usando propriedades de um objeto de localização  
 O código a seguir define as propriedades de um <xref:Microsoft.Office.Interop.Word.Find> objeto para procurar texto dentro da seleção atual. Observe que os critérios de pesquisa, como pesquisa de encaminhamento, encapsulamento e texto para procurar, são propriedades do <xref:Microsoft.Office.Interop.Word.Find> objeto.  
  
 Configuração de cada uma das propriedades do <xref:Microsoft.Office.Interop.Word.Find> objeto não é útil quando você escreve código c#, porque você deve especificar as mesmas propriedades como parâmetros no <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método. Portanto, este exemplo contém código do Visual Basic.  
  
#### <a name="to-set-search-options-using-a-find-object"></a>Para definir opções de pesquisa usando um objeto Find  
  
1.  Definir as propriedades de um <xref:Microsoft.Office.Interop.Word.Find> objeto avance a pesquisa por meio de uma seleção de texto **localizar me**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]  
  
## <a name="using-execute-method-arguments"></a>Usando Execute argumentos de método  
 O código a seguir usa o <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método de um <xref:Microsoft.Office.Interop.Word.Find> objeto para procurar texto dentro da seleção atual. Observe que os critérios de pesquisa, como pesquisa de encaminhamento, encapsulamento e texto para procurar, são passados como parâmetros do <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método.  
  
#### <a name="to-set-search-options-using-execute-method-arguments"></a>Para definir opções de pesquisa usando os argumentos de método Execute  
  
1.  Passe os critérios de pesquisa como parâmetros do <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método para pesquisar uma seleção de texto para a frente **localizar me**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: programaticamente pesquisar e substituir texto em documentos](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Como: programaticamente percorrer itens encontrados em documentos](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Como restaurar seleções após pesquisas de forma programática](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
  
  