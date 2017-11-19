---
title: "Passo a passo: Exibindo a correspondência de chaves | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4a7d122f19e21eebbe5bd598272fb7cb9f52b27
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-displaying-matching-braces"></a>Passo a passo: Exibindo a correspondência de chaves
Você pode implementar recursos de idioma como correspondência definindo as chaves que você deseja corresponder e, em seguida, adicionar uma marca de marcador de texto para correspondência de chaves quando o cursor estiver em uma das chaves de chaves. Você pode definir chaves no contexto de um idioma, você pode definir seu próprio tipo de conteúdo e a extensão de nome do arquivo e aplicar as marcas a apenas esse tipo ou você pode aplicar marcas para um tipo de conteúdo existente (como "texto"). A instrução a seguir mostra como aplicar a chave de correspondência de marcas para o tipo de conteúdo "texto".  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instalar o SDK do Visual Studio no Centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Criando um projeto do Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Para criar um projeto MEF  
  
1.  Crie um projeto de classificação do Editor. Nome da solução `BraceMatchingTest`.  
  
2.  Adicione um modelo de item de classificação de Editor para o projeto. Para obter mais informações, consulte [criando uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Exclua os arquivos de classe existente.  
  
## <a name="implementing-a-brace-matching-tagger"></a>Implementando um marcador de correspondência de chaves  
 Para obter um efeito semelhante ao que é usado no Visual Studio de realce de chave, você pode implementar um marcador do tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. O código a seguir mostra como definir o marcador para os pares de chave em qualquer nível de aninhamento. Neste exemplo, os pares de chave []. [] e {} são definidos no construtor de marcador, mas em uma implementação de linguagem completa os pares de chave relevante seriam definidos na especificação de linguagem.  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>Para implementar um marcador de correspondência de chaves  
  
1.  Adicione um arquivo de classe e nomeie-a correspondência de chaves.  
  
2.  Importe os namespaces a seguir.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]  
  
3.  Definir uma classe `BraceMatchingTagger` que herda de <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> do tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]  
  
4.  Adicione propriedades para a exibição de texto, o buffer de origem e o ponto de instantâneo atual e também um conjunto de pares de chave.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]  
  
5.  No construtor de marcador, defina as propriedades e assinar os eventos de alteração do modo de exibição <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> e <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. Neste exemplo, para fins ilustrativos, os pares correspondentes também são definidos no construtor.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]  
  
6.  Como parte do <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementação, declarar um evento TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]  
  
7.  Os manipuladores de eventos de atualização a atual posição do cursor do `CurrentChar` propriedade e gerar o evento TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]  
  
8.  Implementar o <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> método para que correspondam a chaves quando o caractere atual é uma chave de abertura ou quando o caractere anterior é um colchete de fechamento, como Visual Studio. Quando a correspondência for encontrada, esse método cria duas marcas, um para a chave de abertura e outra para o colchete de fechamento.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]  
  
9. Os seguintes métodos privados localizar a chave correspondente em qualquer nível de aninhamento. O primeiro método localiza o caractere de fechamento que corresponde ao caractere aberto:  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]  
  
10. O método auxiliar a seguir localiza o caractere aberto que corresponde a um caractere de fechamento:  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>Implementando um provedor de marcador de correspondência de chaves  
 Além de implementar um marcador, você também deve implementar e exportar um provedor de marcador. Nesse caso, o tipo de conteúdo do provedor é "text". Isso significa que a correspondência de colchetes aparecerá em todos os tipos de arquivos de texto, mas uma implementação mais completa aplicaria correspondência apenas a um tipo de conteúdo específico de chave.  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>Para implementar um provedor de marcador de correspondência de chaves  
  
1.  Declarar um provedor de marcador que herda de <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, nomeie-o BraceMatchingTaggerProvider e exportá-lo com um <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto" e um <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]  
  
2.  Implementar o <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> método para instanciar um BraceMatchingTagger.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]  
  
## <a name="building-and-testing-the-code"></a>Compilar e testar o código  
 Para testar esse código, compile a solução BraceMatchingTest e executá-lo na instância experimental.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>Para compilar e testar a solução BraceMatchingTest  
  
1.  Compile a solução.  
  
2.  Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é instanciada.  
  
3.  Crie um arquivo de texto e digite algum texto que inclui a correspondência de chaves.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  Quando você posiciona o cursor antes de uma chave de abertura, essa chave e a chave de fechamento correspondente deve estar realçada. Quando você posiciona o cursor logo após o colchete de fechamento, essa chave e a chave de abertura correspondente deve estar realçada.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Vincular um tipo de conteúdo a uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)