---
title: 'Como: adicionar texto e formatação a células em tabelas do Word programaticamente | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- cells, adding text and formatting
- text [Office development in Visual Studio], adding to Word tables
- formatting [Office development in Visual Studio]
- tables [Office development in Visual Studio], adding text and formatting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c7d50a5531bdb4e073c2760ae6d4e746b4970af6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>Como adicionar texto e formatação a células em tabelas do Word programaticamente
  Cada tabela consiste em uma coleção de células. Cada indivíduo <xref:Microsoft.Office.Interop.Word.Cell> objeto representa uma célula na tabela. Você se referir a cada célula por sua localização na tabela. Este exemplo refere-se à célula localizada na primeira linha e a primeira coluna da tabela; adiciona texto à célula; e aplica formatação.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### <a name="to-add-text-and-formatting-to-cells"></a>Para adicionar texto e formatação a células  
  
1.  Fazer referência à célula por sua localização na tabela, adicionar texto à célula e aplique a formatação.  
  
     O exemplo de código a seguir pode ser usado em uma personalização no nível do documento. Para usar este exemplo, executá-la na `ThisDocument` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#97)]  
  
     O exemplo de código a seguir pode ser usado em um suplemento do VSTO. Este exemplo usa o documento ativo. Para usar o exemplo, executá-la na `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#97)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: criar programaticamente tabelas do Word](../vsto/how-to-programmatically-create-word-tables.md)   
 [Como: adicionar programaticamente as linhas e colunas a tabelas do Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Como preencher tabelas do Word com propriedades do documento de forma programática](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  