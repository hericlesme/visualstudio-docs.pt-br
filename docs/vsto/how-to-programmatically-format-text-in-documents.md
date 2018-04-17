---
title: 'Como: Formatar o texto em documentos programaticamente | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a4f356da47a91e0f86f36594ff4254ca0d6ea3e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
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
  
  