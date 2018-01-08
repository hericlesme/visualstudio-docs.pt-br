---
title: "Instruções passo a passo: Estrutura de tópicos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
caps.latest.revision: "30"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 15dd5f0121fca86a38631bf775ec25d4428632e1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-outlining"></a>Instruções passo a passo: estrutura de tópicos
Você pode implementar recursos de linguagem, como a estrutura de tópicos definindo os tipos de regiões de texto que você deseja expandir ou recolher. Você pode definir regiões no contexto de um serviço de idioma, você pode definir seu próprio tipo de conteúdo e a extensão de nome do arquivo e aplica a definição de região a somente esse tipo ou você pode aplicar as definições de região como um tipo de conteúdo existente (como "texto"). Este passo a passo mostra como definir e exibir regiões de estrutura de tópicos.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 A partir do Visual Studio 2015, você não instalar o SDK do Visual Studio no Centro de download. Ele está incluído como um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Criando um projeto do Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Para criar um projeto MEF  
  
1.  Crie um projeto do VSIX. Nome da solução `OutlineRegionTest`.  
  
2.  Adicione um modelo de item de classificação de Editor para o projeto. Para obter mais informações, consulte [criando uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Exclua os arquivos de classe existente.  
  
## <a name="implementing-an-outlining-tagger"></a>Implementando um marcador de estrutura de tópicos  
 Regiões de estrutura de tópicos são marcados por um tipo de marcação (<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>). Essa marca fornece o padrão de comportamento de estrutura de tópicos. A região de contornada pode ser expandida ou recolhida. A região de contornada é marcada por um sinal de adição, se ele estiver recolhido ou um sinal de menos se ele é expandido e a região expandida é delimitada por uma linha vertical.  
  
 As etapas a seguir mostram como definir um marcador que cria as regiões de estrutura de tópicos para todas as regiões são delimitadas por "[" e "]".  
  
#### <a name="to-implement-an-outlining-tagger"></a>Para implementar um marcador de estrutura de tópicos  
  
1.  Adicione um arquivo de classe e denomine- `OutliningTagger`.  
  
2.  Importe os namespaces a seguir.  
  
     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]  
  
3.  Crie uma classe denominada `OutliningTagger`, e a implementar <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>:  
  
     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]  
  
4.  Adicione alguns campos para acompanhar o instantâneo e o buffer de texto e para acumular os conjuntos de linhas que devem ser marcadas como regiões de estrutura de tópicos. Esse código inclui uma lista de objetos de região (a ser definido mais tarde) que representam as regiões de estrutura de tópicos.  
  
     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]  
  
5.  Adicione um construtor de marcador que inicializa os campos, analisa o buffer e adiciona um manipulador de eventos para o <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> evento.  
  
     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]  
  
6.  Implementar o <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> abrange de método, que cria uma instância da marca. Este exemplo supõe que as extensões no <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> passado para o método são contíguas, embora isso possa não ser sempre o caso. Esse método cria um novo intervalo de marca para cada uma das regiões de estrutura de tópicos.  
  
     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]  
  
7.  Declarar um `TagsChanged` manipulador de eventos.  
  
     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]  
  
8.  Adicionar um `BufferChanged` manipulador de eventos que responde a <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> eventos analisando o buffer de texto.  
  
     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]  
  
9. Adicione um método que analisa o buffer. O exemplo fornecido aqui é apenas para fins ilustrativos. Ele analisa o buffer de forma síncrona em regiões de estrutura de tópicos aninhadas.  
  
     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]  
  
10. O método auxiliar a seguir obtém um inteiro que representa o nível de estrutura de tópicos, de forma que 1 é o par de chaves mais à esquerda.  
  
     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]  
  
11. O método auxiliar a seguir converte uma região (definida mais adiante neste tópico) em um SnapshotSpan.  
  
     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]  
  
12. O código a seguir é apenas para fins ilustrativos. Define uma classe PartialRegion que contém o número de linha e o deslocamento do início de uma região de estrutura de tópicos e também uma referência à região do pai (se houver). Isso permite que o analisador configurar aninhados regiões de estrutura de tópicos. Uma classe derivada de região contém uma referência para o número da linha do final de uma região de estrutura de tópicos.  
  
     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]  
  
## <a name="implementing-a-tagger-provider"></a>Implementando um provedor de marcador  
 Você deve exportar um provedor de marcador para o marcador. O provedor de marcador cria um `OutliningTagger` para um buffer de tipo de conteúdo "texto" ou else retorna um `OutliningTagger` se o buffer já tiver um.  
  
#### <a name="to-implement-a-tagger-provider"></a>Para implementar um provedor de marcador  
  
1.  Crie uma classe denominada `OutliningTaggerProvider` que implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>e exportá-lo com os atributos ContentType e TagType.  
  
     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]  
  
2.  Implementar o <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> método adicionando um `OutliningTagger` para as propriedades do buffer.  
  
     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]  
  
## <a name="building-and-testing-the-code"></a>Compilar e testar o código  
 Para testar esse código, compile a solução OutlineRegionTest e executá-lo na instância experimental.  
  
#### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Para compilar e testar a solução OutlineRegionTest  
  
1.  Compile a solução.  
  
2.  Quando você executa este projeto no depurador, uma segunda instância do Visual Studio é instanciada.  
  
3.  Crie um arquivo de texto. Digite qualquer texto que inclui a chave de abertura e a chave de fechamento.  
  
    ```  
    [  
       Hello  
    ]  
    ```  
  
4.  Deve haver uma região de estrutura de tópicos que inclui as duas chaves. Você poderá clicar no sinal de subtração à esquerda da chave de abertura para Recolher região de estrutura de tópicos. Quando a região é recolhido, o símbolo de reticências (...) deve aparecer à esquerda da região recolhida e um pop-up que contém o texto **focalizar texto** deve aparecer quando você move o ponteiro sobre o botão de reticências.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Vincular um tipo de conteúdo a uma extensão de nome de arquivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)