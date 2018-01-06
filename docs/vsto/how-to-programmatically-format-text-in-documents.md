---
title: 'Como: Formatar o texto em documentos programaticamente | Microsoft Docs'
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
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
ms.assetid: 0a84893b-5ccc-4515-a2dc-95773ee8eaba
caps.latest.revision: "42"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 30bc3e878be8667b8ea306bcf7ba3a9648a706c2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-format-text-in-documents"></a>Como formatar texto em documentos programaticamente
  Você pode usar o <xref:Microsoft.Office.Interop.Word.Range> objeto para formatar o texto em um documento do Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 O exemplo a seguir seleciona o primeiro parágrafo no documento e altera o tamanho da fonte, o nome da fonte e o alinhamento. Em seguida, ele seleciona o intervalo e exibe uma caixa de mensagem para pausar antes de executar a próxima seção de código. A seção a seguir chama o método de desfazer do <xref:Microsoft.Office.Tools.Word.Document> item de host (para uma personalização no nível do documento) ou o <xref:Microsoft.Office.Interop.Word.Document> classe (para um Add-in do VSTO) três vezes. Ele aplica o estilo do recuo Normal e exibe uma caixa de mensagem para pausar o código. Em seguida, o código chama o <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> método uma vez e exibe uma caixa de mensagem.  
  
## <a name="document-level-customization-example"></a>Exemplo de personalização de nível de documento  
  
#### <a name="to-format-text-using-a-document-level-customization"></a>Para formatar o texto usando uma personalização no nível do documento  
  
1.  O exemplo a seguir pode ser usado em uma personalização no nível do documento. Para usar esse código, executá-la na `ThisDocument` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#62)]  
  
## <a name="vsto-add-in-example"></a>Exemplo de suplemento do VSTO  
  
#### <a name="to-format-text-using-a-vsto-add-in"></a>Para formatar o texto usando um suplemento do VSTO  
  
1.  O exemplo a seguir pode ser usado em um suplemento do VSTO. Este exemplo usa o documento ativo. Para usar esse código, executá-la na `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#62)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: definir programaticamente e selecionar intervalos em documentos](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Como: programaticamente inserir texto em documentos do Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Como pesquisar e substituir texto em documentos de forma programática](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)  
  
  