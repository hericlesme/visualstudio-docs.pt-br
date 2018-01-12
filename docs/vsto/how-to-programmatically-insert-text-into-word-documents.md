---
title: 'Como: programaticamente inserir texto em documentos do Word | Microsoft Docs'
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
- ranges, inserting text in documents
- text [Office development in Visual Studio], inserting in documents
- ranges, replacing text in documents
- documents [Office development in Visual Studio], inserting text
- text [Office development in Visual Studio], replacing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3e54850bd4cdd66786474f3f823e5e73dc54d344
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-insert-text-into-word-documents"></a>Como inserir texto em documentos do Word programaticamente
  Há três maneiras principais para inserir texto em documentos do Microsoft Office Word:  
  
-   Inserir texto em um intervalo.  
  
-   Substitua texto em um intervalo pelo novo texto.  
  
-   Use o <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> método de um <xref:Microsoft.Office.Interop.Word.Selection> objeto para inserir texto no cursor ou da seleção.  
  
> [!NOTE]  
>  Você também pode inserir texto em controles de conteúdo e indicadores. Para obter mais informações, consulte [controles de conteúdo](../vsto/content-controls.md) e [indicador controle](../vsto/bookmark-control.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="inserting-text-in-a-range"></a>Inserindo texto em um intervalo  
 Use o <xref:Microsoft.Office.Interop.Word.Range.Text%2A> propriedade de um <xref:Microsoft.Office.Interop.Word.Range> objeto para inserir texto em um documento.  
  
#### <a name="to-insert-text-in-a-range"></a>Para inserir texto em um intervalo  
  
1.  Especifique um intervalo no início de um documento e inserir o texto **novo texto**.  
  
     O exemplo de código a seguir pode ser usado em uma personalização no nível do documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#51)]  
  
     O exemplo de código a seguir pode ser usado em um suplemento do VSTO. Esse código usa o documento ativo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#51)]  
  
2.  Selecione o <xref:Microsoft.Office.Interop.Word.Range> objeto, que foi expandida de um caractere para o comprimento do texto inserido.  
  
     [!code-vb[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#52)]
     [!code-csharp[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#52)]  
  
## <a name="replacing-text-in-a-range"></a>Substituindo texto em um intervalo  
 Se o intervalo especificado contiver texto, todo o texto do intervalo é substituído com o texto inserido.  
  
#### <a name="to-replace-text-in-a-range"></a>Para substituir o texto em um intervalo  
  
1.  Criar um <xref:Microsoft.Office.Interop.Word.Range> objeto que consiste em 12 primeiros caracteres do documento.  
  
     O exemplo de código a seguir pode ser usado em uma personalização no nível do documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#53)]  
  
     O exemplo de código a seguir pode ser usado em um suplemento do VSTO. Esse código usa o documento ativo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#53)]  
  
2.  Substitua esses caracteres com a cadeia de caracteres **novo texto**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#54)]
     [!code-csharp[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#54)]  
  
3.  Selecione o intervalo.  
  
     [!code-vb[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#55)]
     [!code-csharp[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#55)]  
  
## <a name="inserting-text-using-typetext"></a>Inserindo texto usando TypeText  
 O <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> método insere texto na seleção. <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>se comporta de maneira diferente dependendo das opções definidas no computador do usuário. O código no procedimento a seguir declara uma <xref:Microsoft.Office.Interop.Word.Selection> variável de objeto e desativa o **sobrescrever** opção se ele está ativado. Se o **sobrescrever** opção é ativada, e qualquer texto ao lado do cursor será substituído.  
  
#### <a name="to-insert-text-using-the-typetext-method"></a>Para inserir texto usando o método TypeText  
  
1.  Declarar um <xref:Microsoft.Office.Interop.Word.Selection> variável de objeto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#57)]
     [!code-csharp[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#57)]  
  
2.  Desativar o **sobrescrever** opção se ele está ativado.  
  
     [!code-vb[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#58)]
     [!code-csharp[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#58)]  
  
3.  Teste para ver se a seleção atual é um ponto de inserção.  
  
     Se for, o código insere uma frase usando <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>e, em seguida, um parágrafo marca usando o <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> método.  
  
     [!code-vb[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#59)]
     [!code-csharp[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#59)]  
  
4.  O código de **ElseIf** bloquear realiza testes para verificar se a seleção é uma seleção normal. Se for, em seguida, outro **se** bloquear realiza testes para verificar se o **ReplaceSelection** opção está ativada. Se for, o código usa o <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> método de seleção para recolher a seleção para um ponto de inserção no início do bloco de texto selecionado. Insira o texto e uma marca de parágrafo.  
  
     [!code-vb[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#60)]
     [!code-csharp[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#60)]  
  
5.  Se a seleção não é um ponto de inserção ou de um bloco de texto selecionado, em seguida, o código de **Else** bloco não fará nada.  
  
     [!code-vb[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#61)]
     [!code-csharp[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#61)]  
  
 Você também pode usar o <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> método o <xref:Microsoft.Office.Interop.Word.Selection> objeto, que simula a funcionalidade da tecla BACKSPACE no teclado. No entanto, quando se trata de inserção e manipulação de texto, o <xref:Microsoft.Office.Interop.Word.Range> objeto oferece mais controle.  
  
 O exemplo a seguir mostra o código completo. Para usar este exemplo, execute o código do `ThisDocument` ou `ThisAddIn` classe em seu projeto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#56)]
 [!code-csharp[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#56)]  
  
## <a name="see-also"></a>Consulte também  
 [Como: Formatar o texto em documentos programaticamente](../vsto/how-to-programmatically-format-text-in-documents.md)   
 [Como: definir programaticamente e selecionar intervalos em documentos](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Como estender intervalos em documentos de forma programática](../vsto/how-to-programmatically-extend-ranges-in-documents.md)  
  
  