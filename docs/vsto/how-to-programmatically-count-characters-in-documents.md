---
title: 'Como: programaticamente contar caracteres em documentos | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4ae05466c871b51d790f1031755be062806fc120
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>Como contar caracteres em documentos programaticamente
  O primeiro caractere em um documento está na posição de caractere 0, que representa o ponto de inserção. A última posição do caractere é igual ao número total de caracteres do documento. Você pode determinar o número de caracteres em um documento usando o <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> propriedade o <xref:Microsoft.Office.Interop.Word.Characters> coleção.  
  
 Todos os caracteres no documento são contados, incluindo espaços, marcas de parágrafo e outros caracteres que normalmente são ocultas. Até mesmo um novo documento em branco retorna uma contagem de um caractere porque ela contém uma marca de parágrafo.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-display-the-number-of-characters-in-a-document-level-customization"></a>Para exibir o número de caracteres em uma personalização no nível do documento  
  
1.  Selecione todo o documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#98)]  
  
2.  Exiba o número de caracteres do documento em uma caixa de mensagem.  
  
     [!code-vb[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#99)]  
  
### <a name="to-display-the-number-of-characters-in-an-vsto-add-in"></a>Para exibir o número de caracteres em um suplemento do VSTO  
  
1.  Selecione todo o documento. O exemplo a seguir seleciona o documento ativo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#98)]  
  
2.  Exiba o número de caracteres do documento em uma caixa de mensagem.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#99)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: recuperar programaticamente caracteres iniciais e finais em intervalos](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Como definir e selecionar intervalos em documentos de forma programática](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)  
  
  