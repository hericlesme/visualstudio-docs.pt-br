---
title: Biblioteca de Visualizador de imagem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ee0be99b307955017b896f70019dfc05481717c9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="image-library-viewer"></a>Visualizador de biblioteca de imagens
A ferramenta do Visualizador de biblioteca do Visual Studio imagem pode carregar e pesquisar os manifestos de imagem, permitindo que o usuário para manipulá-los da mesma maneira que faria do Visual Studio. O usuário pode alterar o plano de fundo, tamanhos, DPI, alto contraste e outras configurações. A ferramenta também exibe informações de carregamento de cada manifesto de imagem e exibe informações de origem de cada imagem no manifesto de imagem. Essa ferramenta é útil para:  
  
1.  Diagnosticando erros  
  
2.  Garantindo atributos estão definidos corretamente nos manifestos de imagem personalizada  
  
3.  Procurando imagens no catálogo de imagem do Visual Studio para que uma extensão do Visual Studio pode usar as imagens que se ajustam o estilo do Visual Studio  
  
 ![Biblioteca herói de Visualizador de imagem](../../extensibility/internals/media/image-library-viewer-hero.png "biblioteca herói de Visualizador de imagem")  
  
 **Moniker de imagem**  
  
 Um moniker de imagem (ou moniker abreviada) é um par de GUID:ID que identifica exclusivamente um ativo de imagem ou um item de lista de imagem na biblioteca de imagens.  
  
 **Arquivos de manifesto de imagem**  
  
 Arquivos de imagem de manifesto (.imagemanifest) são arquivos XML que definem um conjunto de ativos de imagem, os identificadores que representam os ativos e a imagem real ou imagens que representam cada ativo. Manifestos de imagem podem definir imagens autônomas ou listas de imagens para dar suporte da interface do usuário. Além disso, há atributos que podem ser definidos no ativo ou em imagens individuais por trás de cada ativo para alterar quando e como esses ativos são exibidos.  
  
 **Esquema de manifesto de imagem**  
  
 Um manifesto de conclusão de imagem tem esta aparência:  
  
```xml  
<ImageManifest>  
      <!-- zero or one Symbols elements -->  
      <Symbols>  
        <!-- zero or more Guid, ID, or String elements -->  
      </Symbols>  
      <!-- zero or one Images elements -->  
      <Images>  
        <!-- zero or more Image elements -->  
      </Images>  
      <!-- zero or one ImageLists elements -->  
      <ImageLists>  
        <!-- zero or more ImageList elements -->  
      </ImageLists>  
</ImageManifest>  
```  
  
 **Símbolos**  
  
 Como ajudam a facilitar a leitura e a manutenção, o manifesto de imagem pode usar os símbolos para valores de atributo. Símbolos são definidos como este:  
  
```xml  
<Symbols>  
      <Import Manifest="manifest" />  
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />  
      <ID Name="cmdidSaveAll" Value="1000" />  
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />  
</Symbols>  
```  
  
|||  
|-|-|  
|**Subelemento**|**Definição**|  
|Importar|Importa os símbolos do arquivo de manifesto especificado para uso no manifesto do atual.|  
|Guid|O símbolo representa um GUID e deve corresponder a formatação de GUID.|  
|ID|O símbolo representa uma ID e deve ser um inteiro não negativo.|  
|Cadeia de Caracteres|O símbolo representa um valor de cadeia de caracteres arbitrária.|  
  
 Símbolos são referenciados usando a sintaxe $(symbol-name) e diferencia maiusculas de minúsculas:  
  
```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  
  
 Alguns símbolos são predefinidos para todos os manifestos. Eles podem ser usados no atributo do Uri a \<fonte > ou \<importação > elemento aos caminhos de referência no computador local.  
  
|||  
|-|-|  
|**Símbolo**|**Descrição**|  
|CommonProgramFiles|O valor da variável de ambiente % CommonProgramFiles %|  
|LocalAppData|O valor da variável de ambiente % LocalAppData %|  
|ManifestFolder|A pasta que contém o arquivo de manifesto|  
|Meus documentos|O caminho completo da pasta Meus documentos do usuário atual|  
|ProgramFiles|O valor da variável de ambiente % ProgramFiles %|  
|Sistema|A pasta Windows\System32|  
|WinDir|O valor da variável de ambiente % WinDir %|  
  
 **Image**  
  
 O \<imagem > elemento define uma imagem que pode ser referenciada por um identificador de origem. O GUID e ID juntos formam o moniker de imagem. O moniker para a imagem deve ser exclusivo entre a biblioteca de imagem inteira. Se mais de uma imagem tem um moniker determinado, o primeiro encontrado durante a criação de biblioteca é aquele que é mantido.  
  
 Ele deve conter pelo menos uma fonte. Embora fontes de tamanho com neutralidade fornecerá os melhores resultados em uma ampla variedade de tamanhos, eles não são necessários. Se o serviço é solicitado para uma imagem de tamanho não definido na \<imagem > elemento e não há nenhuma fonte com neutralidade de tamanho, o serviço de escolher a melhor fonte de tamanho específico e dimensioná-lo para o tamanho solicitado.  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
  
|||  
|-|-|  
|**Atributo**|**Definição**|  
|Guid|[Obrigatório] A parte GUID do moniker de imagem|  
|ID|[Obrigatório] A parte de identificação do moniker de imagem|  
|AllowColorInversion|[Opcional, padrão Verdadeiro] Indica se a imagem pode ter suas cores invertidas programaticamente quando usado em um plano de fundo escuro.|  
  
 **Source**  
  
 O \<origem > elemento define um ativo de origem de imagem única (XAML e PNG).  
  
```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  
  
|||  
|-|-|  
|**Atributo**|**Definição**|  
|URI|[Obrigatório] Um URI que define onde a imagem pode ser carregada do. Pode ser um dos seguintes:<br /><br /> -A [Pack URI](http://msdn.microsoft.com/en-US/library/aa970069\(v=vs.100\).aspx) usando o aplicativo: / / / autoridade<br /><br /> -Uma referência de recurso do componente absoluto<br /><br /> -Um caminho para um arquivo que contém um recurso nativo|  
|Informações preliminares|[Opcional] Indica o tipo de plano de fundo que a fonte destina-se a ser usado.<br /><br /> Pode ser um dos seguintes:<br /><br /> - *Luz*: A origem pode ser usada em um plano de fundo claro.<br /><br /> - *Escuro*: A origem pode ser usada em um plano de fundo escuro.<br /><br /> - *Alto contraste será*: A origem pode ser usada em qualquer plano de fundo no modo de alto contraste.<br /><br /> - *HighContrastLight*: A fonte pode ser usada no plano de fundo claro no modo de alto contraste.<br /><br /> -*HighContrastDark*: A origem pode ser usada em um plano de fundo escuro no modo de alto contraste.<br /><br /> Se o **em segundo plano** atributo for omitido, a fonte pode ser usada em qualquer plano de fundo.<br /><br /> Se **em segundo plano** é *Light*, *escuro*, *HighContrastLight*, ou *HighContrastDark*, o cores da fonte nunca são invertidas. Se **em segundo plano** for omitido ou definido como *alto contraste será*, inversão de cores da fonte é controlado por uma imagem do **AllowColorInversion** atributo.|  
  
 Um \<origem > elemento pode ter exatamente um dos seguintes subelementos opcionais:  
  
||||  
|-|-|-|  
|**Elemento**|**Atributos (todas obrigatórias)**|**Definição**|  
|\<Tamanho >|Valor|A origem será usada para imagens de determinado tamanho (em unidades de dispositivo). A imagem será quadrada.|  
|\<SizeRange >|MinSize, MaxSize|Inclusive, a origem será usada para imagens de MinSize para MaxSize (em unidades de dispositivo). A imagem será quadrada.|  
|\<Dimensões >|Largura, altura|A origem será usada para imagens de determinada largura e altura (em unidades de dispositivo).|  
|\<DimensionRange >|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|Inclusive, a origem será usada para imagens da largura/altura mínima para a largura/altura máxima (em unidades de dispositivo).|  
  
 Um \<origem > elemento também pode ter um opcional \<NativeResource > subelemento, que define um \<fonte > que é carregado de um assembly nativo em vez de um assembly gerenciado.  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|||  
|-|-|  
|**Atributo**|**Definição**|  
|Tipo|[Obrigatório] O tipo de recurso nativo, XAML ou PNG|  
|ID|[Obrigatório] A parte de ID inteiro do recurso nativo|  
  
 **ImageList**  
  
 O \<ImageList > elemento define uma coleção de imagens que podem ser retornadas em uma única faixa. A faixa é criada sob demanda, conforme necessário.  
  
```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  
  
|||  
|-|-|  
|**Atributo**|**Definição**|  
|Guid|[Obrigatório] A parte GUID do moniker de imagem|  
|ID|[Obrigatório] A parte de identificação do moniker de imagem|  
|Externo|[Opcional, padrão é false] Indica se o moniker de imagem faz referência a uma imagem no manifesto do atual.|  
  
 O moniker para a imagem independente não precisa fazer referência a uma imagem definida no manifesto atual. Se a imagem independente não pode ser encontrada na biblioteca de imagens, uma imagem de alocador de espaço em branco será usada em seu lugar.  
  
## <a name="how-to-use-the-tool"></a>Como usar a ferramenta  
 **Validando um manifesto de imagem personalizada**  
  
 Para criar um manifesto personalizado, é recomendável que você use a ferramenta ManifestFromResources para gerar o manifesto. Para validar o manifesto personalizado, inicie o Visualizador de biblioteca de imagens e selecione Arquivo > Definir caminhos... para abrir a caixa de diálogo diretórios de pesquisa. A ferramenta usará os diretórios de pesquisa para carregar os manifestos de imagem, mas ele também o usará para localizar os arquivos. dll que contêm as imagens em um manifesto, portanto certifique-se de incluem o manifesto e os diretórios DLL nesta caixa de diálogo.  
  
 ![Pesquisa de Visualizador de biblioteca de imagens](../../extensibility/internals/media/image-library-viewer-search.png "biblioteca pesquisa de Visualizador de imagem")  
  
 Clique em **adicionar...**  selecionar novos diretórios de pesquisa para procurar manifestos e suas DLLs correspondentes. A ferramenta lembrará esses diretórios de pesquisa, e pode ser ativados ou desativada, marcando ou desmarcando um diretório.  
  
 Por padrão, a ferramenta tentará localizar o diretório de instalação do Visual Studio e adicionar esses diretórios à lista de diretórios de pesquisa. Você pode adicionar manualmente os diretórios que não encontra a ferramenta.  
  
 Depois que todos os manifestos são carregados, a ferramenta pode ser usada para alternar **em segundo plano** cores, **DPI**, **alto contraste**, ou **escala de cinza** para as imagens para que um usuário pode inspecionar visualmente ativos de imagem para verificar se estão sendo renderizadas corretamente para várias configurações.  
  
 ![Imagem de plano de fundo de Visualizador de biblioteca](../../extensibility/internals/media/image-library-viewer-background.png "a imagem de plano de fundo de Visualizador de biblioteca")  
  
 A cor de plano de fundo pode ser definida como claro, escuro ou um valor personalizado. Selecionar "Cor personalizada" abrir uma caixa de diálogo de seleção de cor e adicionar essa cor personalizada para a parte inferior da caixa de combinação em segundo plano para fácil recuperação posterior.  
  
 ![Cor personalizada do Visualizador de biblioteca de imagens](../../extensibility/internals/media/image-library-viewer-custom-color.png "cor personalizada do Visualizador de biblioteca de imagens")  
  
 Selecionar um moniker de imagem exibe as informações de cada imagem real por trás desse moniker no painel de detalhes de imagem à direita. O painel também permite que os usuários copiar um moniker por nome ou valor de GUID:ID bruto.  
  
 ![Detalhes da imagem biblioteca Visualizador de imagem](../../extensibility/internals/media/image-library-viewer-image-details.png "biblioteca detalhes da imagem de Visualizador de imagem")  
  
 As informações exibidas para cada fonte de imagem incluem o tipo de plano de fundo para exibi-lo, se ele pode ser com tema ou dá suporte a alto contraste, quais são os tamanhos é válido para ou se ela é neutro de tamanho, e se a imagem é proveniente de um assembly nativo.  
  
 ![Visualizador de biblioteca de imagens pode tema](../../extensibility/internals/media/image-library-viewer-can-theme.png "Visualizador da biblioteca de imagens pode tema")  
  
 Ao validar um manifesto de imagem, é recomendável que você implantar o manifesto e imagem DLL em seus locais do mundo real. Isso vai verificar se todos os caminhos relativos estão funcionando corretamente e que a biblioteca de imagens pode localizar e carregar o manifesto e imagem DLL.  
  
 **Pesquisa de catálogo de imagem KnownMonikers**  
  
 Para atender melhor às estilo do Visual Studio, uma extensão do Visual Studio pode usar as imagens no catálogo de imagem do Visual Studio em vez de criar e usar seu próprio. Isso tem a vantagem de não ter de manter as imagens e garante que a imagem terá uma imagem de backup de alto DPI para que ele deve ser correto em todas as configurações de DPI que dá suporte ao Visual Studio.  
  
 O Visualizador de biblioteca de imagem permite que um manifesto a ser pesquisada para que um usuário possa localizar o identificador de origem que representa um ativo de imagem e usar esse identificador de origem no código. Para pesquisar imagens, digite o termo de pesquisa desejado na caixa de pesquisa e pressione Enter. A barra de status na parte inferior exibirá quantas correspondências foram encontradas fora do total de imagens em todos os manifestos.  
  
 ![Filtro de Visualizador de biblioteca de imagens](../../extensibility/internals/media/image-library-viewer-filter.png "filtro do Visualizador de biblioteca de imagens")  
  
 Ao procurar por identificadores de imagem nos manifestos existentes, recomendamos que você pesquise e use somente identificadores de origem do Visual Studio imagem do catálogo, outros identificadores intencionalmente publicamente acessíveis ou suas própria monikers personalizados. Se você usar identificadores confidenciais, interface do usuário personalizada pode ser interrompida ou tem suas imagens alteradas de maneiras inesperadas se ou quando os identificadores confidenciais e imagens são alteradas ou atualizadas.  
  
 Além disso, é possível pesquisar por GUID. Esse tipo de pesquisa é útil para filtrar a lista para um único manifesto ou subseção única de um manifesto de manifesto se que contém vários GUIDs.  
  
 ![Imagem de filtro do Visualizador de biblioteca GUID](../../extensibility/internals/media/image-library-viewer-filter-guid.png "biblioteca visualizador filtro GUID da imagem")  
  
 Por fim, pesquisa por ID é possível também.  
  
 ![ID do filtro de Visualizador de biblioteca de imagens](../../extensibility/internals/media/image-library-viewer-filter-id.png "identificação da biblioteca de filtro Visualizador de imagem")  
  
## <a name="notes"></a>Observações  
  
-   Por padrão, a ferramenta extrairá nos vários manifestos de imagem presentes no diretório de instalação do Visual Studio. É o único que tem monikers publicamente consumíveis a **Microsoft.VisualStudio.ImageCatalog** de manifesto. GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 (fazer **não** substituir esse GUID em um manifesto personalizado) tipo: KnownMonikers  
  
-   A ferramenta de tentativas no início para carregar todos os manifestos de imagem encontra, portanto, pode levar vários segundos para o aplicativo é exibida realmente. Também pode ser lento ou não responde ao carregar os manifestos.  
  
## <a name="sample-output"></a>Saída de Exemplo  
 Essa ferramenta não gera nenhuma saída.