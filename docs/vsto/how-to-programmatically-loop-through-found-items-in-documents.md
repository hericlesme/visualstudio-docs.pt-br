---
title: 'Como: programaticamente percorrer itens encontrados em documentos | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- loops, through found items in documents
- documents [Office development in Visual Studio], searching
- text [Office development in Visual Studio], searching in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 660434790ab4bf3073a00f2ec7ab9db737381707
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-loop-through-found-items-in-documents"></a>Como percorrer itens encontrados em documentos programaticamente
  O <xref:Microsoft.Office.Interop.Word.Find> classe tiver um <xref:Microsoft.Office.Interop.Word.Find.Found%2A> propriedade, que retorna **true** sempre que um item pesquisado for encontrado. Você pode executar um loop através de todas as instâncias encontradas em uma <xref:Microsoft.Office.Interop.Word.Range> usando o <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-loop-through-found-items"></a>Para percorrer itens encontrados  
  
1.  Declarar uma <xref:Microsoft.Office.Interop.Word.Range> objeto.  
  
     O exemplo de código a seguir pode ser usado em uma personalização no nível do documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#79)]
     [!code-csharp[Trin_VstcoreWordAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#79)]  
  
     O exemplo de código a seguir pode ser usado em um suplemento do VSTO. Este exemplo usa o documento ativo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#79)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#79](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#79)]  
  
2.  Use o <xref:Microsoft.Office.Interop.Word.Find.Found%2A> propriedade em um loop para pesquisar todas as ocorrências da cadeia de caracteres do documento e incrementar uma variável de inteiro de 1 a cada vez que a cadeia de caracteres for encontrada.  
  
     [!code-vb[Trin_VstcoreWordAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#80)]
     [!code-csharp[Trin_VstcoreWordAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#80)]  
  
3.  Exiba o número de vezes que a cadeia de caracteres foi encontrada em uma caixa de mensagem.  
  
     [!code-vb[Trin_VstcoreWordAutomation#81](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#81)]
     [!code-csharp[Trin_VstcoreWordAutomation#81](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#81)]  
  
 Os exemplos a seguir mostram o método complete.  
  
## <a name="document-level-customization-example"></a>Exemplo de personalização de nível de documento  
  
#### <a name="to-loop-through-items-in-a-document-level-customization"></a>Para executar um loop através de itens em uma personalização no nível do documento  
  
1.  O exemplo a seguir mostra o código completo para uma personalização no nível do documento. Para usar esse código, executá-la na `ThisDocument` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#78)]
     [!code-csharp[Trin_VstcoreWordAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#78)]  
  
## <a name="vsto-add-in-example"></a>Exemplo de suplemento do VSTO  
  
#### <a name="to-loop-through-items-in-an-vsto-add-in"></a>Para executar um loop através de itens em um suplemento do VSTO  
  
1.  O exemplo a seguir mostra o código completo para um suplemento do VSTO. Para usar esse código, executá-la na `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#78)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#78](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#78)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: programaticamente pesquisar e substituir texto em documentos](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Como: definir opções de pesquisa no Word](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Como: definir programaticamente e selecionar intervalos em documentos](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Como: programaticamente restaurar seleções após pesquisas](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  