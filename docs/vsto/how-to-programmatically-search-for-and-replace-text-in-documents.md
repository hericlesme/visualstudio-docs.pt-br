---
title: 'Como: programaticamente pesquisar e substituir texto em documentos | Microsoft Docs'
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
- documents [Office development in Visual Studio], searching
- text searches, replacing text
- text searches, documents
- text [Office development in Visual Studio], searching in documents
- text [Office development in Visual Studio], text searches
ms.assetid: a66962f5-eeb9-4dc6-a70f-9039ab437a63
caps.latest.revision: "51"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4d3b5523bdf6d851f7822a7123575b2903b45a2a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-search-for-and-replace-text--in-documents"></a>Como localizar e substituir texto em documentos programaticamente
  O <xref:Microsoft.Office.Interop.Word.Find> objeto é um membro de ambos os <xref:Microsoft.Office.Interop.Word.Selection> e o <xref:Microsoft.Office.Interop.Word.Range> objetos e você pode usar qualquer um para pesquisar texto em documentos do Microsoft Office Word. O comando Substituir é uma extensão do comando Localizar.  
  
 Use um <xref:Microsoft.Office.Interop.Word.Find> para loop por meio de um documento do Microsoft Office Word e pesquisa de texto específico, formatação ou estilo e usa o <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> propriedade para substituir qualquer um dos itens encontrados.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="using-a-selection-object"></a>Usando um objeto de seleção  
 Quando você usa um <xref:Microsoft.Office.Interop.Word.Selection> objeto localizar texto, qualquer pesquisa critérios especificados são aplicados apenas no momento o texto selecionado. Se o <xref:Microsoft.Office.Interop.Word.Selection> é um ponto de inserção, em seguida, o documento será pesquisado. Quando o item for encontrado que corresponda aos critérios de pesquisa, ela é selecionada automaticamente.  
  
 É importante observar que o <xref:Microsoft.Office.Interop.Word.Find> critérios são cumulativos, o que significa que os critérios são adicionados aos critérios de pesquisa anterior. Limpar formatação de pesquisas anteriores usando o <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> método antes da pesquisa.  
  
#### <a name="to-find-text-using-a-selection-object"></a>Para localizar texto usando um objeto de seleção  
  
1.  Atribua uma cadeia de caracteres de pesquisa a uma variável.  
  
     [!code-vb[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#68)]
     [!code-csharp[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#68)]  
  
2.  Limpe formatação de pesquisas anteriores.  
  
     [!code-vb[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#69)]
     [!code-csharp[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#69)]  
  
3.  Executa a pesquisa e exibe uma caixa de mensagem com os resultados.  
  
     [!code-vb[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#70)]
     [!code-csharp[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#70)]  
  
 O exemplo a seguir mostra o método complete.  
  
 [!code-vb[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#67)]
 [!code-csharp[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#67)]  
  
## <a name="using-a-range-object"></a>Usando um objeto de intervalo  
 Usando um <xref:Microsoft.Office.Interop.Word.Range> objeto permite que você procure texto sem exibir nada na interface do usuário. O <xref:Microsoft.Office.Interop.Word.Find> objeto retorna **True** se o texto for encontrado que corresponda aos critérios de pesquisa, e **False** se não existir. Ela também redefine o <xref:Microsoft.Office.Interop.Word.Range> objeto para corresponder aos critérios de pesquisa, se o texto for encontrado.  
  
#### <a name="to-find-text-using-a-range-object"></a>Para localizar texto usando um objeto de intervalo  
  
1.  Definir um <xref:Microsoft.Office.Interop.Word.Range> objeto que consiste o segundo parágrafo no documento.  
  
     O exemplo de código a seguir pode ser usado em uma personalização no nível do documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#72)]
     [!code-csharp[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#72)]  
  
     O exemplo de código a seguir pode ser usado em um suplemento do VSTO. Este exemplo usa o documento ativo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#72)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#72)]  
  
2.  Usando o <xref:Microsoft.Office.Interop.Word.Range.Find%2A> propriedade o <xref:Microsoft.Office.Interop.Word.Range> do objeto, primeiro desmarque todas as opções de formatação existente e, em seguida, procure a cadeia de caracteres **localizar me**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#73)]
     [!code-csharp[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#73)]  
  
3.  Exibir os resultados da pesquisa em uma caixa de mensagem e selecione o <xref:Microsoft.Office.Interop.Word.Range> para torná-lo visível.  
  
     [!code-vb[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#74)]
     [!code-csharp[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#74)]  
  
     Se a pesquisa falhar, o segundo parágrafo está selecionado. Se tiver êxito, os critérios de pesquisa são exibidos.  
  
 O exemplo a seguir mostra o código completo para uma personalização no nível do documento. Para usar este exemplo, execute o código do `ThisDocument` classe em seu projeto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#71)]
 [!code-csharp[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#71)]  
  
 O exemplo a seguir mostra o código completo para um suplemento do VSTO. Para usar este exemplo, execute o código do `ThisAddIn` classe em seu projeto.  
  
 [!code-vb[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#71)]
 [!code-csharp[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#71)]  
  
## <a name="searching-for-and-replacing-text-in-documents"></a>Pesquisando e substituindo texto em documentos  
 O código a seguir pesquisa a seleção atual e substitui todas as ocorrências da cadeia de caracteres **localizar me** com a cadeia de caracteres **encontrado**.  
  
#### <a name="to-search-for-and-replace-text-in-documents"></a>Para pesquisar e substituir texto em documentos  
  
1.  Adicione o seguinte código de exemplo para o `ThisDocument` ou `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#75)]
     [!code-csharp[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#75)]  
  
     O <xref:Microsoft.Office.Interop.Word.Find> classe tiver um <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> método e o <xref:Microsoft.Office.Interop.Word.Replacement> classe também tem seu próprio <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A> método. Quando você estiver executando operações de localizar e substituir, você deve usar o método ClearFormatting dos dois objetos. Se você usá-lo somente no <xref:Microsoft.Office.Interop.Word.Find> do objeto, você pode obter resultados inesperados no texto de substituição.  
  
2.  Use o <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> método o <xref:Microsoft.Office.Interop.Word.Find> objeto para substituir cada item encontrado. Para especificar quais itens para substituir, use o *substituir* parâmetro. Esse parâmetro pode ser um dos seguintes <xref:Microsoft.Office.Interop.Word.WdReplace> valores:  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll>substitui todos os itens localizados.  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone>substitui a nenhum dos itens encontrados.  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne>substitui o primeiro item encontrado.  
  
## <a name="see-also"></a>Consulte também  
 [Como: definir opções de pesquisa no Word](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Como: programaticamente percorrer itens encontrados em documentos](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Como: definir programaticamente e selecionar intervalos em documentos](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Como: programaticamente restaurar seleções após pesquisas](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  