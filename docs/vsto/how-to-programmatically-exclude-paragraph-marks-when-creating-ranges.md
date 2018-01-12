---
title: "Como: excluir programaticamente marcas de parágrafo ao criar intervalos | Microsoft Docs"
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
- documents [Office development in Visual Studio], excluding paragraphs
- ranges, excluding paragraph marks in Word
- documents [Office development in Visual Studio], paragraph marks
- paragraphs, controlling structure
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 37af64898686da4f09730f5b46fbbfa0936ddd0e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-exclude-paragraph-marks-when-creating-ranges"></a>Como excluir marcas de parágrafo ao criar intervalos programaticamente
  Sempre que você criar um <xref:Microsoft.Office.Interop.Word.Range> objeto com base em um parágrafo, todos os caracteres não imprimíveis, como marcas de parágrafo, estão incluídos no intervalo. Você talvez queira inserir o texto de um parágrafo de origem em um parágrafo de destino. Se você não deseja dividir o parágrafo de destino em parágrafos diferentes, deverá primeiro remover a marca de parágrafo do parágrafo fonte. Além disso, como as informações de formatação de parágrafo é armazenado dentro da marca de parágrafo, não convém incluí-lo quando você insere o intervalo em um parágrafo existente.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 O procedimento de exemplo a seguir declara duas variáveis de cadeia de caracteres, recupera o conteúdo dos parágrafos primeiro e o segundo no documento ativo e, em seguida, troca seu conteúdo. O exemplo demonstra, em seguida, removendo o marcador de parágrafo do intervalo com o <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> método e a inserção de texto no parágrafo.  
  
### <a name="to-control-paragraph-structure-when-inserting-text"></a>Para controlar a estrutura de parágrafo ao inserir texto  
  
1.  Crie duas variáveis de intervalo para o primeiro e o segundo parágrafo e recuperar seu conteúdo usando o <xref:Microsoft.Office.Interop.Word.Range.Text%2A> propriedade.  
  
     O exemplo de código a seguir pode ser usado em uma personalização no nível do documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#27)]  
  
     O exemplo de código a seguir pode ser usado em um suplemento do VSTO do nível do aplicativo. Esse código usa o documento ativo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#27)]  
  
2.  Atribuir o <xref:Microsoft.Office.Interop.Word.Range.Text%2A> propriedade trocar o texto entre dois parágrafos.  
  
     [!code-vb[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#28)]
     [!code-csharp[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#28)]  
  
3.  Selecione cada intervalo separadamente e pausar para exibir os resultados em uma caixa de mensagem.  
  
     [!code-vb[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#29)]
     [!code-csharp[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#29)]  
  
4.  Ajustar `firstRange` usando o <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> método para que o marcador de parágrafo não faz parte de `firstRange`.  
  
     [!code-vb[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#30)]
     [!code-csharp[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#30)]  
  
5.  Substitua o restante do texto no primeiro parágrafo, atribuir uma nova cadeia de caracteres para o <xref:Microsoft.Office.Interop.Word.Range.Text%2A> propriedade do intervalo.  
  
     [!code-vb[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#31)]
     [!code-csharp[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#31)]  
  
6.  Substitua o texto da `secondRange`, incluindo a marca de parágrafo.  
  
     [!code-vb[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#32)]
     [!code-csharp[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#32)]  
  
7.  Selecione `firstRange` pausar para exibir os resultados em uma caixa de mensagem e, em seguida, faça o mesmo com `secondRange`.  
  
     Como `firstRange` foi redefinido para excluir a marca de parágrafo, a formatação original do parágrafo é preservada. No entanto, uma frase foi inserida sobre a marca de parágrafo em `secondRange`, removendo o parágrafo separado.  
  
     [!code-vb[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#33)]
     [!code-csharp[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#33)]  
  
     O conteúdo original de ambos os intervalos foram salvas como cadeias de caracteres, para que você possa restaurar o documento para sua condição original.  
  
8.  Reajustar `firstRange` para incluir a marca de parágrafo, usando o <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> método para a posição de um caractere.  
  
     [!code-vb[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#34)]
     [!code-csharp[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#34)]  
  
9. Excluir `secondRange`. Isso restaura o parágrafo 3 à sua posição original.  
  
     [!code-vb[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#35)]
     [!code-csharp[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#35)]  
  
10. Restaurar o texto de parágrafo original em `firstRange`.  
  
     [!code-vb[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#36)]
     [!code-csharp[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#36)]  
  
11. Use o <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> método o <xref:Microsoft.Office.Interop.Word.Range> objeto para inserir o conteúdo de dois de parágrafo após `firstRange`e, em seguida, selecione `firstRange`.  
  
     [!code-vb[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#37)]
     [!code-csharp[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#37)]  
  
## <a name="document-level-customization-example"></a>Exemplo de personalização de nível de documento  
  
#### <a name="to-control-paragraph-structure-when-inserting-text-in-document-level-customizations"></a>Para controlar a estrutura de parágrafo ao inserir um texto em personalizações no nível do documento  
  
1.  O exemplo a seguir mostra o método complete uma personalização de nível de documento. Para usar esse código, executá-la na `ThisDocument` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#26)]  
  
## <a name="vsto-add-in-example"></a>Exemplo de suplemento do VSTO  
  
#### <a name="to-control-paragraph-structure-when-inserting-text-in-an-vsto-add-in"></a>Para controlar a estrutura de parágrafo ao inserir um texto em um suplemento do VSTO  
  
1.  O exemplo a seguir mostra o método de conclusão de um suplemento do VSTO. Para usar esse código, executá-la na `ThisAddIn` classe em seu projeto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#26)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: estender a intervalos em documentos programaticamente](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Como: programaticamente recolher intervalos ou seleções em documentos](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Como: programaticamente inserir texto em documentos do Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Como: programaticamente redefinir intervalos em Word documentos](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Como: definir programaticamente e selecionar intervalos em documentos](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  