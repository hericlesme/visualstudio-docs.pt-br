---
title: 'Como: definir programaticamente e selecionar intervalos em documentos | Microsoft Docs'
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
- documents [Office development in Visual Studio], selecting sentences
- documents [Office development in Visual Studio], ranges
- sentences, selecting in documents
- ranges, selecting in documents
- ranges, defining in documents
ms.assetid: 0727c1cb-d44c-4f1c-a699-4365dd13be5d
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2fcc1b96607c36fdfbc2f9940a7b7984b3b299fa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-define-and-select-ranges-in-documents"></a>Como definir e selecionar intervalos em documentos programaticamente
  Você pode definir um intervalo em um documento do Microsoft Office Word usando um <xref:Microsoft.Office.Interop.Word.Range> objeto. Você pode selecionar todo o documento de diversas maneiras, por exemplo, usando o <xref:Microsoft.Office.Interop.Word.Range.Select%2A> método do <xref:Microsoft.Office.Interop.Word.Range> de objeto, ou usando a propriedade de conteúdo do <xref:Microsoft.Office.Tools.Word.Document> classe (uma personalização no nível do documento) ou o <xref:Microsoft.Office.Interop.Word.Document> classe (em um Suplemento do VSTO).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="defining-a-range"></a>Definindo um intervalo  
 O exemplo a seguir mostra como criar um novo <xref:Microsoft.Office.Interop.Word.Range> objeto que inclui as primeiras sete caracteres no documento ativo, incluindo caracteres não imprimíveis. Ele seleciona o texto dentro do intervalo.  
  
#### <a name="to-define-a-range-in-a-document-level-customization"></a>Para definir um intervalo em uma personalização no nível do documento  
  
1.  Adicionar o intervalo para o documento, passando um caractere de início e término para o <xref:Microsoft.Office.Tools.Word.Document.Range%2A> método o <xref:Microsoft.Office.Tools.Word.Document> classe. Para usar este exemplo de código, executá-la na `ThisDocument` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#18)]  
  
#### <a name="to-define-a-range-by-using-a-vsto-add-in"></a>Para definir um intervalo usando um suplemento do VSTO  
  
1.  Adicionar o intervalo para o documento, passando um caractere de início e término para o <xref:Microsoft.Office.Interop.Word._Document.Range%2A> método o <xref:Microsoft.Office.Interop.Word.Document> classe. O exemplo de código a seguir adiciona um intervalo para o documento ativo. Para usar este exemplo de código, executá-la na `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#18)]  
  
## <a name="selecting-a-range-in-a-document-level-customization"></a>Selecionando um intervalo em uma personalização no nível do documento  
 Os exemplos a seguir mostram como selecionar todo o documento usando o <xref:Microsoft.Office.Interop.Word.Range.Select%2A> método de um <xref:Microsoft.Office.Interop.Word.Range> do objeto, ou usando o <xref:Microsoft.Office.Tools.Word.Document.Content%2A> propriedade o <xref:Microsoft.Office.Tools.Word.Document> classe.  
  
#### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Para selecionar todo o documento como um intervalo por meio do método Select  
  
1.  Use o <xref:Microsoft.Office.Interop.Word.Range.Select%2A> método de um <xref:Microsoft.Office.Interop.Word.Range> que contém o documento inteiro. Para usar o exemplo de código a seguir, executá-la na `ThisDocument` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#19)]  
  
#### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Para selecionar todo o documento como um intervalo usando a propriedade de conteúdo  
  
1.  Use o <xref:Microsoft.Office.Tools.Word.Document.Content%2A> propriedade para definir um intervalo que abrange todo o documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#20)]
     [!code-csharp[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#20)]  
  
 Você também pode usar os métodos e propriedades de outros objetos para definir um intervalo.  
  
#### <a name="to-select-a-sentence-in-the-active-document"></a>Para selecionar uma frase no documento ativo  
  
1.  Definir o intervalo usando os <xref:Microsoft.Office.Interop.Word.Sentences> coleção. Use o índice da frase que você deseja selecionar.  
  
     [!code-vb[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#21)]
     [!code-csharp[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#21)]  
  
 É outra maneira de selecionar uma frase definir manualmente os valores de início e término do intervalo.  
  
#### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Para selecionar uma frase, defina manualmente os valores de início e término  
  
1.  Crie uma variável de intervalo.  
  
     [!code-vb[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#23)]  
  
2.  Verifique se há pelo menos duas frases no documento, defina o *iniciar* e *final* argumentos de intervalo e, em seguida, selecione o intervalo.  
  
     [!code-vb[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#24)]  
  
## <a name="selecting-a-range-by-using-a-vsto-add-in"></a>Selecionar um intervalo usando um suplemento do VSTO  
 Os exemplos a seguir mostram como selecionar todo o documento usando o <xref:Microsoft.Office.Interop.Word.Range.Select%2A> método de um <xref:Microsoft.Office.Interop.Word.Range> do objeto, ou usando o <xref:Microsoft.Office.Interop.Word._Document.Content%2A> propriedade o <xref:Microsoft.Office.Interop.Word.Document> classe.  
  
#### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Para selecionar todo o documento como um intervalo por meio do método Select  
  
1.  Use o <xref:Microsoft.Office.Interop.Word.Range.Select%2A> método de um <xref:Microsoft.Office.Interop.Word.Range> que contém o documento inteiro. O exemplo de código a seguir seleciona o conteúdo do documento ativo. Para usar este exemplo de código, executá-la na `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#19)]  
  
#### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Para selecionar todo o documento como um intervalo usando a propriedade de conteúdo  
  
1.  Use o <xref:Microsoft.Office.Interop.Word._Document.Content%2A> propriedade para definir um intervalo que abrange todo o documento.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#20)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#20)]  
  
 Você também pode usar os métodos e propriedades de outros objetos para definir um intervalo.  
  
#### <a name="to-select-a-sentence-in-the-active-document"></a>Para selecionar uma frase no documento ativo  
  
1.  Definir o intervalo usando os <xref:Microsoft.Office.Interop.Word.Sentences> coleção. Use o índice da frase que você deseja selecionar.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#21)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#21)]  
  
 É outra maneira de selecionar uma frase definir manualmente os valores de início e término do intervalo.  
  
#### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Para selecionar uma frase, defina manualmente os valores de início e término  
  
1.  Crie uma variável de intervalo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#23)]  
  
2.  Verifique se há pelo menos duas frases no documento, defina o *iniciar* e *final* argumentos de intervalo e, em seguida, selecione o intervalo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#24)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do modelo de objeto do Word](../vsto/word-object-model-overview.md)   
 [Como: estender a intervalos em documentos programaticamente](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Como: recuperar programaticamente caracteres iniciais e finais em intervalos](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Como: estender a intervalos em documentos programaticamente](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Como: programaticamente redefinir intervalos em Word documentos](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Como: programaticamente recolher intervalos ou seleções em documentos](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Como excluir marcas de parágrafo ao criar intervalos de forma programática](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  
  