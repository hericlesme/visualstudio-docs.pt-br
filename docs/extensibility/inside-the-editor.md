---
title: Dentro do Editor | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
caps.latest.revision: "31"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1876f334ad1b444b464ecc420767dea90baed6b3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="inside-the-editor"></a>Dentro do Editor
O editor é composto de um número de subsistemas diferentes, que são projetados para impedir que o editor de texto separado de modelo a exibição de texto e a interface do usuário.  
  
 Estas seções descrevem os diferentes aspectos do editor:  
  
-   [Visão geral dos subsistemas](../extensibility/inside-the-editor.md#overview)  
  
-   [O modelo de texto](../extensibility/inside-the-editor.md#textmodel)  
  
-   [A exibição de texto](../extensibility/inside-the-editor.md#textview)  
  
 Estas seções descrevem os recursos do editor:  
  
-   [As marcas e classificadores](../extensibility/inside-the-editor.md#tagsandclassifiers)  
  
-   [Adornos](../extensibility/inside-the-editor.md#adornments)  
  
-   [Projeção](../extensibility/inside-the-editor.md#projection)  
  
-   [Estrutura de tópicos](../extensibility/inside-the-editor.md#outlining)  
  
-   [Associações de mouse](../extensibility/inside-the-editor.md#mousebindings)  
  
-   [Operações do Editor](../extensibility/inside-the-editor.md#editoroperations)  
  
-   [IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
##  <a name="overview"></a>Visão geral dos subsistemas  
  
### <a name="text-model-subsystem"></a>Subsistema do modelo de texto  
 O subsistema de modelo de texto é responsável por que representa o texto e habilitar sua manipulação. O subsistema de modelo de texto contém o <xref:Microsoft.VisualStudio.Text.ITextBuffer> interface, que descreve a sequência de caracteres que devem ser exibidos pelo editor. Esse texto pode ser modificado, rastreado e manipulado de várias maneiras. O modelo de texto também fornece tipos para os seguintes aspectos:  
  
-   Um serviço que associa a arquivos de texto e gerencia lendo e gravando-los no sistema de arquivos.  
  
-   Um serviço diferencial que localiza as diferenças mínimas entre duas sequências de objetos.  
  
-   Um sistema usado para descrever o texto em um buffer em termos de subconjuntos do texto em outros buffers.  
  
 O subsistema de modelo de texto é livre de conceitos de interface do usuário. Por exemplo, não é responsável por formatação de texto ou o layout de texto, e ele não tem conhecimento de ornamentos visual que possam estar associados com o texto.  
  
 Os tipos públicos do subsistema de modelo de texto estão contidos no Microsoft.VisualStudio.Text.Data.dll e Microsoft.VisualStudio.CoreUtilitiy.dll, que depende apenas de biblioteca de classe base do .NET Framework e o Managed Extensibility Framework (MEF).  
  
### <a name="text-view-subsystem"></a>Subsistema do modo de exibição de texto  
 O subsistema do modo de exibição de texto é responsável por formatação e exibição de texto. Os tipos neste subsistema são divididos em duas camadas, dependendo se os tipos se baseiam no Windows Presentation Foundation (WPF). Os tipos mais importantes são <xref:Microsoft.VisualStudio.Text.Editor.ITextView> e <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>, que controlam o conjunto de linhas de texto que devem ser exibidas e também o cursor, a seleção e os recursos para o adorno de texto usando elementos de UI do WPF. Este subsistema também fornece a área de exibição de margens ao redor do texto. Essas margens podem ser estendidas e podem conter tipos diferentes de efeitos visuais e conteúdos. Exemplos de margens são linha número exibe e barras de rolagem.  
  
 Os tipos públicos do subsistema de modo de exibição de texto estão contidos no Microsoft.VisualStudio.Text.UI.dll e Microsoft.VisualStudio.Text.UI.Wpf.dll. O primeiro conjunto contém os elementos de independente de plataforma e o segundo contém os elementos específicos de WPF.  
  
### <a name="classification-subsystem"></a>Subsistema de classificação  
 O subsistema de classificação é responsável por determinar propriedades de fonte para texto. Um classificador quebra o texto em classes diferentes, por exemplo, "palavra-chave" ou "comment". O mapa de formatação de classificação se relaciona essas classes para propriedades de fonte real, por exemplo, "azul Consolas 10 pt". Essas informações são usadas pelo modo de exibição de texto quando formata e renderiza o texto. Marcação, que é descrito em mais detalhes posteriormente neste tópico, permite que os dados a serem associados com intervalos de texto.  
  
 Os tipos públicos do subsistema de classificação estão contidos em Microsoft.VisualStudio.Text.Logic.dll, e eles interagem com os aspectos visuais de classificação, que estão contidos em Microsoft.VisualStudio.Text.UI.Wpf.dll.  
  
### <a name="operations-subsystem"></a>Subsistema de operações  
 O subsistema de operações define o comportamento do editor. Ele fornece a implementação de comandos de editor do Visual Studio e o sistema de desfazer.  
  
## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Examinar mais detalhadamente o modelo de texto e a exibição de texto  
  
###  <a name="textmodel"></a>O modelo de texto  
 O subsistema de modelo de texto consiste em diferentes grupos de tipos de texto. Isso inclui o buffer de texto, os instantâneos de texto e os intervalos de texto.  
  
#### <a name="text-buffers-and-text-snapshots"></a>Buffers de texto e texto instantâneos  
 O <xref:Microsoft.VisualStudio.Text.ITextBuffer> interface representa uma sequência de caracteres Unicode que são codificados usando UTF-16, que é a codificação usada pelo `String` tipo do .NET Framework. Um buffer de texto pode ser persistente como um documento do sistema de arquivo, mas isso não é necessário.  
  
 O <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> é usado para criar um buffer de texto vazio ou um buffer de texto que é inicializado a partir de uma cadeia de caracteres ou <xref:System.IO.TextReader>. O buffer de texto pode ser transmitido para o sistema de arquivos como um <xref:Microsoft.VisualStudio.Text.ITextDocument>.  
  
 O buffer de texto pode ser editado por qualquer thread até que um thread se apropria de buffer de texto chamando <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>. Depois disso, somente esse thread pode executar edições.  
  
 Um buffer de texto pode passar por várias versões durante seu ciclo de vida. Uma nova versão é gerada sempre que o buffer é editado e uma imutável <xref:Microsoft.VisualStudio.Text.ITextSnapshot> representa o conteúdo dessa versão do buffer. Como os instantâneos de texto são imutáveis, você pode acessar um instantâneo de texto em qualquer thread, sem restrições, mesmo se o buffer de texto que representa continua sendo alterada.  
  
#### <a name="text-snapshots-and-text-snapshot-lines"></a>Instantâneos de texto e linhas de instantâneo de texto  
 Você pode exibir o conteúdo de um instantâneo de texto como uma cadeia de caracteres ou como uma sequência de linhas. Caracteres e as linhas são que ambas indexada começando com zero. Um instantâneo de texto vazio contém caracteres e uma linha vazia. Uma linha é delimitada por qualquer sequência de caracteres de quebra de linha Unicode válida ou o início ou fim do buffer. Caracteres de quebra de linha explicitamente são representados no instantâneo de texto e as quebras de linha em um instantâneo de texto não tiverem o mesmo.  
  
> [!NOTE]
>  Para obter mais informações sobre caracteres de quebra de linha no editor do Visual Studio, consulte [codificações e quebras de linha](../ide/encodings-and-line-breaks.md).  
  
 Uma linha de texto é representada por um <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> objeto, que pode ser obtido a partir de um instantâneo de texto para um número de linha específico ou para uma posição de caracteres em particular.  
  
#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints, SnapshotSpans e NormalizedSnapshotSpanCollections  
 Um <xref:Microsoft.VisualStudio.Text.SnapshotPoint> representa uma posição de caractere em um instantâneo. A posição é garantia de estar entre zero e o comprimento do instantâneo. Um <xref:Microsoft.VisualStudio.Text.SnapshotSpan> representa um intervalo de texto em um instantâneo. Sua posição final é garantia de estar entre zero e o comprimento do instantâneo. O <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> consiste em um conjunto de <xref:Microsoft.VisualStudio.Text.SnapshotSpan> objetos do mesmo instantâneo.  
  
#### <a name="spans-and-normalizedspancollections"></a>Intervalos e NormalizedSpanCollections  
 Um <xref:Microsoft.VisualStudio.Text.Span> representa um intervalo que pode ser aplicado a um intervalo de texto em um instantâneo de texto. Posições de instantâneo são com base em zero, para que podem iniciar intervalos em qualquer posição como zero. O `End` propriedade de uma extensão é igual à soma dos seus `Start` propriedade e seu `Length` propriedade. Um `Span` não inclui o caractere que é indexado pelo `End` propriedade. Por exemplo, um intervalo que tem início = 5 e comprimento = 3 tem fim = 8, e inclui os caracteres em posições 5, 6 e 7. A notação para este alcance é 5..8).  
  
 Dois intervalos de interseção se eles têm qualquer posições em comum, incluindo a posição final. Portanto, a interseção de [3, 5) e [2, 7) é [3, 5) e a interseção de [3, 5) e [5, 7) é [5, 5). (Observe que [5, 5) é um intervalo vazio.)  
  
 Dois intervalos sobreponham, se eles têm posições em comum, exceto para a posição final. Um intervalo vazio nunca se sobrepõe a qualquer outro período, e a sobreposição de duas extensões nunca está vazia.  
  
 A <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> é uma lista de extensões na ordem as propriedades de início das extensões. Na lista de intervalos sobrepostos ou adjacentes serão mesclados. Por exemplo, considerando o conjunto de intervalos de [5..9), [0..1), [3..6), e [9..10), a lista normalizada de intervalos é [0..1), [3..10).  
  
#### <a name="itextedit-textversion-and-text-change-notifications"></a>ITextEdit, TextVersion e notificações de alteração de texto  
 O conteúdo de um buffer de texto pode ser alterado usando um <xref:Microsoft.VisualStudio.Text.ITextEdit> objeto. Criando esse tipo de objeto (usando um do `CreateEdit()` métodos de <xref:Microsoft.VisualStudio.Text.ITextBuffer>) inicia uma transação de texto que consiste em edições de texto. Cada edição é uma substituição de algum intervalo de texto no buffer por uma cadeia de caracteres. As coordenadas e o conteúdo de cada edição são expressos em relação ao instantâneo do buffer, quando a transação foi iniciada. O <xref:Microsoft.VisualStudio.Text.ITextEdit> objeto ajusta as coordenadas de edições que são afetadas por outras edições na mesma transação.  
  
 Por exemplo, considere um buffer de texto que contém essa cadeia de caracteres:  
  
```  
abcdefghij  
```  
  
 Aplicar uma transação que contém duas edições, uma edição que substitui a extensão em [2..4) usando o caractere `X` e uma segunda edição que substitui a extensão em [6..9) usando o caractere `Y`. O resultado é esse buffer:  
  
```  
abXefYj  
```  
  
 As coordenadas para a segunda edição foram computadas em relação ao conteúdo do buffer no início da transação, antes que a primeira edição foi aplicada.  
  
 As alterações para o buffer em vigor quando o <xref:Microsoft.VisualStudio.Text.ITextEdit> objeto está confirmado chamando seu `Apply()` método. Se não houver pelo menos uma edição de não vazio, um novo <xref:Microsoft.VisualStudio.Text.ITextVersion> é criado, um novo <xref:Microsoft.VisualStudio.Text.ITextSnapshot> é criado e um `Changed` é gerado. Cada versão de texto tem um instantâneo de texto. Um instantâneo de texto representa o estado de conclusão do buffer de texto depois de uma transação de edição, mas uma versão de texto descreve somente as alterações de um instantâneo para a próxima. Em geral, os instantâneos de texto são deve ser usado uma vez e depois são descartados, enquanto as versões de texto devem permanecer ativa por algum tempo.  
  
 Uma versão de texto contém uma <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>. Esta coleção descreve as alterações que, quando aplicado ao instantâneo, irá gerar o instantâneo subsequente. Cada <xref:Microsoft.VisualStudio.Text.ITextChange> na coleção contém a posição do caractere de alteração, a cadeia de caracteres de substituição e a cadeia de caracteres de substituição. A cadeia de caracteres de substituição está vazia para uma inserção básica e a cadeia de caracteres de substituição está vazia para uma exclusão básico. A coleção normalizada é sempre `null` para a versão mais recente do buffer de texto.  
  
 Apenas uma <xref:Microsoft.VisualStudio.Text.ITextEdit> objeto pode ser instanciado para um buffer de texto a qualquer momento, e todas as edições de texto devem ser executadas no thread que possui o buffer de texto (se a propriedade tenha sido solicitada). Uma edição de texto pode ser abandonada chamando seu `Cancel` método ou seu `Dispose` método.  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer>também fornece `Insert()`, `Delete()`, e `Replace()` métodos semelhantes aos encontrados no <xref:Microsoft.VisualStudio.Text.ITextEdit> interface. Chamar esses tem o mesmo efeito que criar um <xref:Microsoft.VisualStudio.Text.ITextEdit> objeto, fazendo a chamada semelhante e, em seguida, aplicar a edição.  
  
#### <a name="tracking-points-and-tracking-spans"></a>Pontos de controle e intervalos de rastreamento  
 Um <xref:Microsoft.VisualStudio.Text.ITrackingPoint> representa uma posição de caractere em um buffer de texto. Se o buffer for editado de maneira que faz com que a posição do caractere a ser deslocado, o ponto de controle se desloca com ele. Por exemplo, se um ponto de controle se refere à posição 10 em um buffer e cinco caracteres são inseridos no início do buffer, o ponto de controle, em seguida, refere-se à posição 15. Se uma inserção ocorrer em precisamente a posição indicada pelo ponto de controle, seu comportamento é determinado pelo seu <xref:Microsoft.VisualStudio.Text.PointTrackingMode>, que pode ser `Positive` ou `Negative`. Se o modo de controle for positivo, que o ponto de controle refere-se para o mesmo caractere, que agora está no final da inserção; Se o modo de controle for negativo, o ponto de controle se refere ao primeiro caractere inserido na posição original. Se o caractere na posição que é representado por um ponto de controle for excluído, o ponto de controle muda para o primeiro caractere que segue o intervalo excluído. Por exemplo, se um ponto de controle se refere ao caractere na posição 5, e os caracteres em posições 3 a 6 são excluídos, o ponto de controle refere-se para o caractere na posição 3.  
  
 Um <xref:Microsoft.VisualStudio.Text.ITrackingSpan> representa um intervalo de caracteres em vez de apenas uma posição. Seu comportamento é determinado pelo seu <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>. Se o modo de controle de alcance é <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, aumenta o alcance de controle para incorporar o texto inserido em suas bordas; se o modo de controle de alcance é <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, o período de controle não incorpora o texto inserido em suas bordas. No entanto, se o modo de controle de alcance é <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, uma inserção envia a posição atual em direção ao início e se o modo de controle de alcance <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, uma inserção envia a posição atual no final.  
  
 Você pode obter a posição de um ponto de controle ou o alcance de um período de controle para qualquer instantâneo de buffer de texto à qual pertencem. Pontos de controle e intervalos de rastreamento podem ser consultados com segurança de qualquer thread.  
  
#### <a name="content-types"></a>Tipos de conteúdo  
 Tipos de conteúdo são um mecanismo para definir diferentes tipos de conteúdo. Um tipo de conteúdo pode ser um tipo de arquivo, como "texto", "código" ou "binário", ou um tipo de tecnologia, como "xml", "vb" ou "c#". Por exemplo, a palavra "using" é uma palavra-chave em c# e Visual Basic, mas não em outras linguagens de programação. Portanto, a definição da palavra-chave this poderia ser limitada aos tipos de conteúdo "c#" e "vb".  
  
 Tipos de conteúdo são usados como um filtro de adornos e outros elementos do editor. Muitos recursos do editor e pontos de extensão são definidos por tipo de conteúdo. Por exemplo, a coloração de texto é diferente para arquivos de texto sem formatação, arquivos XML e arquivos de código de origem do Visual Basic. Buffers de texto geralmente são atribuídos a um tipo de conteúdo quando eles são criados e o tipo de conteúdo de um buffer de texto pode ser alterado.  
  
 Tipos de conteúdo podem herdar múltiplo de outros tipos de conteúdo. O <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> permite que você especifique vários tipos base como o pai de um determinado tipo de conteúdo.  
  
 Os desenvolvedores podem definir seus próprios tipos de conteúdo e registrá-los usando o <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>. Muitos recursos do editor podem ser definidos em relação a um tipo específico de conteúdo usando o <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>. Por exemplo, margens de editor, ornamentos e manipuladores de mouse podem ser definidos para que elas se aplicam somente aos editores que exibem tipos específicos de conteúdo.  
  
###  <a name="textview"></a>A exibição de texto  
 A parte de modo de exibição do padrão de controller (MVC) de modo de exibição de modelo define a exibição de texto, a formatação do modo de exibição, os elementos gráficos, como a barra de rolagem e o cursor. Todos os elementos de apresentação do editor do Visual Studio são baseados em WPF.  
  
#### <a name="text-views"></a>Modos de exibição de texto  
 O <xref:Microsoft.VisualStudio.Text.Editor.ITextView> interface é uma representação independente de plataforma de uma exibição de texto. Ele é usado principalmente para exibir documentos de texto em uma janela, mas ele também pode ser usado para outras finalidades, por exemplo, em uma dica de ferramenta.  
  
 A exibição de texto faz referência a tipos diferentes de buffers de texto. O <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> propriedade se refere a um <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> objeto que aponta para esses três buffers de texto diferente: o buffer de dados, que é o buffer de dados de nível superior, o buffer de edição, em que a edição ocorre e o buffer de visual, que é o buffer que está exibido na exibição de texto.  
  
 O texto é formatado com base em classificadores que estão anexados ao buffer de texto subjacente e é adornado usando os provedores de adorno anexados para o modo de texto.  
  
#### <a name="the-text-view-coordinate-system"></a>O sistema de coordenadas de modo de exibição de texto  
 O sistema de coordenadas de modo de exibição de texto Especifica posições no modo de exibição de texto. No sistema de coordenadas, o valor de x 0.0 corresponde com a borda esquerda do texto que está sendo exibido e o valor de y 0.0 corresponde à borda superior do texto que está sendo exibido. A coordenada x aumenta da esquerda para a direita e a coordenada y aumenta de cima para baixo.  
  
 Um visor (a parte do texto visível na janela de texto) não pode ser rolado da mesma maneira horizontal como verticalmente rolado. Um visor é rolado na horizontal, alterando sua coordenada esquerda para que ele se move em relação à superfície de desenho. No entanto, um visor pode ser rolado verticalmente apenas alterando o texto renderizado, o que faz com que um <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> evento ser gerado.  
  
 Distâncias no sistema de coordenadas correspondem aos pixels lógicos. Se a superfície de renderização de texto será exibida sem uma transformação de escala, uma unidade no sistema de coordenadas de renderização de texto corresponde a um pixel na tela.  
  
#### <a name="margins"></a>Margens  
 O <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> interface representa uma margem e habilita o controle da visibilidade de margem e seu tamanho. Há quatro margens predefinidas, que são nomeadas "Top", "Esquerda", "Direita" e "Inferior" e estão conectadas à parte superior, inferior, esquerda ou borda direita de uma exibição. Essas margens são contêineres no qual outros margens podem ser colocadas. A interface define métodos que retornam o tamanho da margem e a visibilidade de uma margem. As margens são elementos visuais que fornecem informações adicionais sobre o modo de exibição de texto para o qual eles estão conectados. Por exemplo, a margem de número de linha exibe os números de linha para a exibição de texto. A margem de glifo exibe elementos de interface do usuário.  
  
 O <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> interface trata a criação e o posicionamento das margens. Margens podem ser solicitadas em relação à outra margem. Margens de prioridade mais alta estão localizadas próximo à exibição de texto. Por exemplo, se existem dois margens esquerdas, margem A e B de margem e margem B tem uma prioridade inferior a margem A, B de margem aparece à esquerda da margem A.  
  
#### <a name="the-text-view-host"></a>O Host do modo de exibição de texto  
 O <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> interface contém a exibição de texto e qualquer decorações adjacentes que acompanham o modo de exibição, por exemplo, as barras de rolagem. O host do modo de exibição de texto também contém as margens que estão anexadas a uma borda da exibição.  
  
#### <a name="formatted-text"></a>Texto formatado  
 O texto que é exibido em uma exibição de texto é composto de <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> objetos. Cada linha da exibição de texto corresponde a uma linha de texto no modo de exibição de texto. Longas linhas no buffer de texto subjacente podem ser parcialmente obscurecidas (se a quebra automática não estiver habilitada) ou divididas em várias linhas de exibição de texto. O <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> interface contém métodos e propriedades para o mapeamento entre as coordenadas e caracteres e para os ornamentos que podem ser associados à linha.  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>objetos são criados usando um <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> interface. Se você estiver preocupado apenas com o texto que é exibido atualmente no modo de exibição, você pode ignorar a origem da formatação. Se você estiver interessado no formato de texto que não é exibido no modo de exibição (por exemplo, para dar suporte a um rich text recortar e colar), você pode usar <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> para formatar o texto em um buffer de texto.  
  
 Formatos de exibição de texto de um <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> por vez.  
  
## <a name="editor-features"></a>Recursos do Editor  
 Os recursos do editor são projetados para que a definição do recurso é separada da sua implementação. O editor inclui os seguintes recursos:  
  
-   As marcas e classificadores  
  
-   Adornos  
  
-   Projeção  
  
-   Estrutura de tópicos  
  
-   Associações de mouse e a chave  
  
-   Operações e primitivos  
  
-   IntelliSense  
  
###  <a name="tagsandclassifiers"></a>As marcas e classificadores  
 Marcas são marcadores que estão associados um intervalo de texto. Podem ser apresentados de maneiras diferentes, por exemplo, usando cores de texto, sublinhados, gráficos ou pop-ups. Classificadores são um tipo de marca.  
  
 Outros tipos de marcas são <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> para realce de texto, <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> para a estrutura de tópicos, e <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> para erros de compilação.  
  
#### <a name="classification-types"></a>Tipos de classificação  
 Um <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> interface representa uma classe de equivalência, que é uma categoria abstrata de texto. Tipos de classificação podem herdar múltiplo de outros tipos de classificação. Por exemplo, a classificações de linguagem de programação pode incluir "palavra-chave", "comment" e "identificador", que herda de "código". Tipos de classificação de idioma natural podem incluir "substantivo", "verbo" e "adjetivo", que herda de "idioma natural".  
  
#### <a name="classifications"></a>Classificações  
 Uma classificação é uma instância de um tipo específico de classificação, normalmente em um intervalo de texto. A <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> é usada para representar uma classificação. Uma extensão de classificação pode ser pensada como um rótulo que abrange um intervalo específico de texto e informa ao sistema que este trecho de texto é de um tipo específico de classificação.  
  
#### <a name="classifiers"></a>Classificadores  
 Um <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> é um mecanismo que quebra o texto em um conjunto de classificações. Classificadores devem ser definidos para tipos de conteúdo específicos e instanciados para buffers de texto específico. Os clientes devem implementar <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> para participar de classificação de texto.  
  
#### <a name="classifier-aggregators"></a>Agregador de classificação  
 Um agregador de classificação é um mecanismo que combina classificadores de buffer de um texto em apenas um conjunto de classificações. Por exemplo, um classificador c# e um classificador do idioma inglês podem criar classificações sobre um comentário em um arquivo c#. Considere este comentário:  
  
```  
// This method produces a classifier  
```  
  
 Um classificador c# pode rotular o período inteiro como um comentário e a classificação do idioma inglês pode classificar "produz" como "verbo" e "method" como "substantivo". O agregador produz um conjunto de classificações não sobrepostos e o tipo do conjunto de baseia-se a todas as contribuições.  
  
 Um agregador de classificação também é um classificador porque quebra o texto em um conjunto de classificações. O agregador de classificação também garante que não há nenhuma sobreposição classificações e que as classificações são classificadas. Classificadores individuais são gratuitos retornar um conjunto de classificações, em qualquer ordem e sobreposição de qualquer forma.  
  
#### <a name="classification-formatting-and-text-coloring"></a>Cores de texto e formatação de classificação  
 Formatação de texto é um exemplo de um recurso que se baseia em classificação de texto. Ele é usado pela camada de modo de exibição de texto para determinar a exibição do texto em um aplicativo. A área de formatação de texto é dependente de WPF, mas a definição de lógica de classificação não é.  
  
 Um formato de classificação é um conjunto de propriedades para um tipo de classificação específicas de formatação. Esses formatos herdam o formato do pai do tipo de classificação.  
  
 Um <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> é um mapa de um tipo de classificação para um conjunto de propriedades de formatação de texto. A implementação do mapa do formato no editor manipula todas as exportações de formatos de classificação.  
  
###  <a name="adornments"></a>Adornos  
 Adornos são efeitos gráficos que não estão diretamente relacionados a fonte e a cor dos caracteres na exibição de texto. Por exemplo, o sublinhado Rabisco vermelho que é usado para marcar não compilar o código em muitas linguagens de programação é um adorno inserido e dicas de ferramenta são ornamentos pop-up. Adornos são derivados de <xref:System.Windows.UIElement> e implementar <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Dois tipos especializados de marca de adorno são o <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, para ornamentos que ocupam o mesmo espaço que o texto em uma exibição, e o <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>, para o sublinhado Rabisco.  
  
 Adornos inseridos são gráficos que fazem parte do modo de exibição de texto formatado. Eles são organizados em diferentes camadas de ordem Z. Há três camadas internas, da seguinte maneira: texto, o cursor e a seleção. No entanto, os desenvolvedores podem definir mais camadas e colocá-los na ordem em relação um ao outro. Os três tipos de adornos inseridos são ornamentos relativos a texto (que move quando move o texto e são excluídas quando o texto é excluído), ornamentos relativos a exibição (que têm a ver com texto não partes da exibição) e controlado pelo proprietário ornamentos (os desenvolvedor deve gerenciar sua colocação).  
  
 Pop-up ornamentos são gráficos que aparecem em uma janela pequena acima da exibição de texto, por exemplo, as dicas de ferramenta.  
  
###  <a name="projection"></a>Projeção  
 Projeção é uma técnica para a criação de um tipo de buffer de texto que não armazena, na verdade, texto, mas em vez disso, combina o texto dos outros buffers de texto diferente. Por exemplo, um buffer de projeção pode ser usado para concatenar o texto dos dois outros buffers e apresentará o resultado como se ele está em um buffer, ou para ocultar partes do texto em um buffer. Um buffer de projeção pode agir como um buffer de origem para outro buffer de projeção. Um conjunto de buffers que são relacionadas pela projeção pode ser construído para reorganizar o texto de várias maneiras diferentes. (Esse conjunto também é conhecido como um *gráfico buffer*.) O recurso de estrutura de tópicos de texto do Visual Studio é implementado usando um buffer de projeção para ocultar o texto recolhido e o editor do Visual Studio para páginas ASP.NET usa projeção para oferecer suporte a idiomas inseridos, como Visual Basic e c#.  
  
 Um <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> é criado usando <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>. Um buffer de projeção é representado por uma sequência ordenada de <xref:Microsoft.VisualStudio.Text.ITrackingSpan> objetos que são conhecidos como *intervalos de origem*. O conteúdo desses intervalos é apresentado como uma cadeia de caracteres. Os buffers de texto do qual as extensões de origem são desenhadas são nomeados *buffers de origem*. Os clientes de um buffer de projeção não precisa estar ciente de que ele difere de um buffer de texto comum.  
  
 O buffer de projeção escuta para eventos de alteração de texto em buffers de origem. Quando o texto em uma fonte abrangem as alterações, o buffer de projeção mapeia as coordenadas de texto alterado para seus próprio coordenadas e gera eventos de alteração de texto apropriado. Por exemplo, considere os buffers de origem A e B que têm esse conteúdo:  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 Se o buffer de projeção P é formado por dois intervalos de texto, um que tenha todos os buffers A e a outros que tem todos os buffers B, P tem o seguinte conteúdo:  
  
```  
P: ABCDEvwxyz  
```  
  
 Se a subcadeia de caracteres `xy` é excluído do buffer B, em seguida, o buffer P gera um evento que indica que os caracteres em posições 7 e 8 foram excluídos.  
  
 O buffer de projeção também pode ser editado diretamente. Ele propaga edições aos buffers de origem apropriada. Por exemplo, se uma cadeia de caracteres é inserida no buffer P na posição 6 (a posição original do caractere "v"), a inserção é propagada ao buffer B na posição 1.  
  
 Há restrições sobre os intervalos de origem que contribuem para um buffer de projeção. Não podem se sobrepor os intervalos de origem; não é possível mapear um local em um buffer de projeção para mais de um local em qualquer buffer de origem e um local em um buffer de origem não é possível mapear mais de um local em um buffer de projeção. Nenhum circularities são permitidas na relação de buffer de origem.  
  
 Os eventos são gerados quando o conjunto de origem armazena em buffer para alterações de buffer uma projeção e quando o conjunto de origem contém alterações.  
  
 Um buffer de corrotina é um tipo especial de buffer de projeção. Ele é usado principalmente para a estrutura de tópicos e operações que expandir e recolher blocos de texto. Um buffer de corrotina baseia-se apenas um buffer de origem e as extensões no buffer de corrotina devem ser ordenadas o mesmo que eles serão ordenados no buffer de origem.  
  
##### <a name="the-buffer-graph"></a>O gráfico de Buffer  
 O <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> interface permite que o mapeamento entre um gráfico de buffers de projeção. Todos os buffers de projeção e buffers de texto são coletados em um gráfico acíclico direcionado, bem como a árvore de sintaxe abstrata produzido por um compilador de linguagem. O gráfico é definido pelo buffer superior, que pode ser qualquer buffer de texto. O gráfico de buffer pode ser mapeado de um ponto no buffer superior a um ponto em um buffer de origem ou de uma extensão do buffer superior a um conjunto de extensões em um buffer de origem. Da mesma forma, ele pode mapear um ponto ou variam de um buffer de origem para um ponto no buffer superior. Gráficos de buffer são criados usando o <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>.  
  
##### <a name="events-and-projection-buffers"></a>Eventos e Buffers de projeção  
 Quando um buffer de projeção é modificado, as modificações são enviadas do buffer de projeção para os buffers que dependem dele. Depois que todos os buffers são modificados, são gerados eventos de alteração de buffer, iniciando com o buffer de nível mais profundo.  
  
###  <a name="outlining"></a>Estrutura de tópicos  
 Estrutura de tópicos é a capacidade de expandir ou recolher diferentes blocos de texto em uma exibição de texto. Estrutura de tópicos é definida como um tipo de <xref:Microsoft.VisualStudio.Text.Tagging.ITag>, na mesma maneira que ornamentos são definidos. A <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> é uma marca que define uma região de texto que pode ser expandida ou recolhida. Para usar a estrutura de tópicos, você deve importar o <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> para obter um <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>. Enumera o Gerenciador de estrutura de tópicos, recolhe e expande os diferentes blocos, que são representados como <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> objetos e gera eventos adequadamente.  
  
###  <a name="mousebindings"></a>Associações de mouse  
 Associações de mouse vincular movimentos de mouse a comandos diferentes. As associações de mouse são definidas usando um <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>, e as associações de chave são definidas usando um <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>. O <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> automaticamente todas as associações de instancia e conecta-se para eventos de mouse no modo de exibição.  
  
 O <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> interface contém manipuladores de eventos de pós-processamento e pré-processar para eventos de mouse diferente. A alça de um dos eventos, você pode substituir alguns dos métodos na <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>.  
  
###  <a name="editoroperations"></a>Operações do Editor  
 Operações do Editor podem ser usadas para automatizar a interação com o editor, para scripts ou outros propósitos. Você pode importar o <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> para operações de acesso em um determinado <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Você pode usar esses objetos para modificar a seleção, rolar a exibição ou mover o cursor para diferentes partes da exibição.  
  
###  <a name="intellisense"></a>IntelliSense  
 O IntelliSense dá suporte a conclusão de instrução, a Ajuda de assinatura (também conhecido como informações de parâmetro), informações rápidas e lâmpadas.  
  
 Conclusão de instrução fornece listas pop-up de conclusões potenciais para nomes de método, os elementos XML e outros elementos de codificação ou marcação. Em geral, um gesto do usuário invoca uma sessão de conclusão. A sessão exibe a lista de possíveis conclusões e o usuário pode selecionar um ou descartar a lista. O <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> é responsável por criar e disparar o <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>. O <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> calcula o <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> de itens de conclusão para a sessão.  
  
## <a name="see-also"></a>Consulte também  
 [Serviço de linguagem e pontos de extensão de Editor](../extensibility/language-service-and-editor-extension-points.md)   
 [Importações do editor](../extensibility/editor-imports.md)