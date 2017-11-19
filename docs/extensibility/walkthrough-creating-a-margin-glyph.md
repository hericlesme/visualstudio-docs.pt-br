---
title: 'Passo a passo: Criando um glifo de margem | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 94c4b602b29bb86acaf1b910075913abcfc79ac0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-margin-glyph"></a>Passo a passo: Criando um glifo de margem
Você pode personalizar a aparência das margens do editor usando extensões de editor personalizado. Este passo a passo coloca um glifo personalizado na margem do indicador, sempre que a palavra "todo" é exibida em um comentário do código.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instalar o SDK do Visual Studio no Centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Criando um projeto MEF  
  
1.  Crie um projeto c# VSIX. (No **novo projeto** caixa de diálogo, selecione **Visual C# / extensibilidade**, em seguida, **projeto VSIX**.) Nome da solução `TodoGlyphTest`.  
  
2.  Adicione um item de projeto do classificador de Editor. Para obter mais informações, consulte [criando uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Exclua os arquivos de classe existente.  
  
## <a name="defining-the-glyph"></a>Definindo o glifo  
 Definir um glifo Implementando o <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> interface.  
  
#### <a name="to-define-the-glyph"></a>Para definir o glifo  
  
1.  Adicione um arquivo de classe e denomine- `TodoGlyphFactory`.  
  
2.  Adicione o seguinte usando as declarações.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  Adicione uma classe denominada `TodoGlyphFactory` que implementa <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  Adicione um campo particular que define as dimensões do glifo.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  Implementar `GenerateGlyph` definindo o elemento de interface do usuário do usuário de glifo. `TodoTag`é definido mais adiante neste passo a passo.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  Adicione uma classe denominada `TodoGlyphFactoryProvider` que implementa <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Exportar esta classe com uma <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "TodoGlyph", um <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de VsTextMarker depois, um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "código" e um <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  Implementar o <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> método instanciando a `TodoGlyphFactory`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Definição de uma marca de tarefas e marcador  
 Defina a relação entre o elemento de interface do usuário que você definiu nas etapas anteriores e margem do indicador, criando um tipo de marca e o marcador e exportá-lo usando um provedor de marcador.  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>Para definir uma marca de tarefas e o marcador  
  
1.  Adicione um novo arquivo de classe ao projeto e denomine- `TodoTagger`.  
  
2.  Adicione a seguir importa.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  Adicione uma classe denominada `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  Modifique a classe denominada `TodoTagger` que implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> do tipo `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  Para o `TodoTagger` classe, adicionar campos privados para um <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> e para o texto a ser localizado na classificação abrange.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  Adicione um construtor que define o classificador.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  Implementar o <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> método localizando todos os a classificação abrange cujos nomes incluem a palavra "Comentários" e cujo texto inclui o texto de pesquisa. Sempre que o texto de pesquisa for encontrado, gerar novamente uma nova <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> do tipo `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  Declarar um `TagsChanged` eventos.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. Adicione uma classe denominada `TodoTaggerProvider` que implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>e exportá-lo com um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "código" e um <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. Importar o <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. Implementar o <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> método instanciando a `TodoTagger`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## <a name="building-and-testing-the-code"></a>Compilar e testar o código  
 Para testar esse código, compile a solução TodoGlyphTest e executá-lo na instância experimental.  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Para compilar e testar a solução TodoGlyphTest  
  
1.  Compile a solução.  
  
2.  Execute o projeto, pressionando F5. Uma segunda instância do Visual Studio é instanciada.  
  
3.  Certifique-se de que a margem de indicador está mostrando. (No **ferramentas** menu, clique em **opções**. No **Editor de texto** página, certifique-se de que **margem do indicador** está selecionada.)  
  
4.  Abra um arquivo de código que tem comentários. Adicione a palavra "todo" para uma das seções de comentário.  
  
5.  Um círculo azul claro que tem um contorno azul escuro deve aparecer na margem do indicador à esquerda da janela de código.