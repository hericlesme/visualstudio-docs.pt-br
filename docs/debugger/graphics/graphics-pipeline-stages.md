---
title: Estágios de Pipeline gráficos | Microsoft Docs
ms.custom: ''
ms.date: 02/09/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.pipeline
ms.assetid: 2bf5c12e-2a00-401c-8163-4e373d08ad3f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c708320442c32158ef193ccf7f08669882135d82
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="graphics-pipeline-stages"></a>Estágios de Pipeline Gráficos
A janela estágios de Pipeline gráficos ajuda a entender como uma chamada de desenho individuais é transformada por cada estágio do pipeline de gráficos do Direct3D.  
  
 Esta é a janela estágios de Pipeline:  
  
 ![Um objeto 3D atravessa os estágios de pipeline.](media/gfx_diag_demo_pipeline_stages_orientation.png)
  
## <a name="understanding-the-graphics-pipeline-stages-window"></a>Noções básicas sobre a janela Estágios de Pipeline Gráficos  
 Janela estágios de Pipeline visualiza o resultado de cada estágio do pipeline de gráficos separadamente, cada chamada de desenho. Normalmente, os resultados dos estágios no meio do pipeline estão ocultos, tornando difícil saber onde um problema de processamento é iniciado. Visualizando separadamente cada estágio, janela estágios de Pipeline torna fácil ver onde o problema começa — por exemplo, você pode ver facilmente quando o estágio de sombreador de vértice inesperadamente faz com que um objeto a ser desenhado fora da tela.  
  
 Depois de identificar o estágio em que o problema ocorrer, você pode usar outras ferramentas do analisador de gráficos para examinar como os dados foram interpretados ou transformados. Problemas de renderização que aparecem nos estágios de pipeline são geralmente descritores de formato de vértice relacionado ao incorreto, programas de sombreador com bugs ou estado configuradas incorretamente.  
  
### <a name="links-to-related-graphics-objects"></a>Links para os objetos gráficos relacionados  
 Contexto adicional, às vezes, é necessário para determinar por que uma chamada de desenho interage de uma maneira específica com o pipeline de gráficos. Para facilitar a localização de neste contexto adicional, os links de janela estágios de Pipeline gráficos para um ou mais objetos que fornecem contexto adicional relacionado ao que está acontecendo no pipeline de gráficos.  
  
-   Direct3D 12 esse objeto é geralmente uma lista de comandos.  
  
-   Direct3D 11 esse objeto é geralmente um contexto de dispositivo de gráficos.  
  
 Esses links são parte da assinatura atual do evento gráficos que está localizada no canto superior esquerdo da janela estágios de Pipeline gráficos. Seguir qualquer um desses links para examinar os detalhes adicionais sobre o objeto.  
  
### <a name="viewing-and-debugging-shader-code"></a>Exibição e depuração do código do sombreador  
 Você pode examinar e depurar o código de vértice, convexa, domínio, sombreadores de pixel e geometria usando os controles na parte inferior dos seus respectivos estágios na janela estágios de Pipeline.  
  
#### <a name="to-view-a-shaders-source-code"></a>Para exibir o código-fonte do sombreador  
  
-   No **estágios de Pipeline gráficos** janela, localize o estágio de sombreador correspondente para o sombreador você deseja examinar. Em seguida, abaixo da imagem de visualização, siga o link de título de estágio de sombreador — por exemplo, siga o link **obj:30 de sombreador de vértice** para exibir o código de origem de sombreador de vértice.  
  
    > [!TIP]
    >  O número de objeto **obj:30**, identifica este sombreador em toda a interface de analisador de gráficos como a janela de histórico de tabela e de pixel do objeto.  
  
#### <a name="to-debug-a-shader"></a>Para depurar um sombreador  
  
-   No **estágios de Pipeline gráficos** janela, localize o estágio de sombreador correspondente para o sombreador você deseja depurar. Em seguida, abaixo da imagem de visualização, escolha **iniciar depuração**. Esse ponto de entrada para os padrões de depurador HLSL para a primeira invocação do sombreador para o estágio correspondente — ou seja, o primeiro pixel, vértice ou primitivo que é processado pelo sombreador durante essa chamada draw. Invocações deste sombreador para um pixel específico ou vértice podem ser acessadas por meio de **histórico de Pixel gráfico**.  
  
### <a name="the-pipeline-stages"></a>Os estágios de pipeline  
 Janela estágios de Pipeline visualiza apenas os estágios do pipeline que estavam ativos durante a chamada de desenho. Cada estágio do pipeline de gráficos transforma uma entrada de estágio anterior e passa o resultado para o próximo estágio. O primeiro estágio – o Assembler de entrada — extrai dados de índice e vértice de seu aplicativo como sua entrada; o último estágio — a fusão de saída — combina renderizado pixels junto com o conteúdo atual do framebuffer recentemente ou destino de renderização como sua saída para produzir a imagem final que você vê na tela.  
  
> [!NOTE]
>  Os sombreadores de computação não têm suporte no **estágios de Pipeline gráficos** janela.  
  
 **Assembler de entrada**  
 O Assembler de entrada lê os dados de índice e vértice especificados pelo seu aplicativo e monta-lo para o hardware de gráficos.  
  
 Na janela estágios de Pipeline, a saída do Assembler de entrada é visualizada como um modelo de wireframe. Para fazer uma análise detalhada de resultados, selecione **Assembler de entrada** no **estágios de Pipeline gráficos** janela para exibir os vértices montados em 3D completo usando o Editor de modelo.  
  
> [!NOTE]
>  Se o `POSITION` semântica não está presente na saída do assembler de entrada e, em seguida, nada é exibido no **Assembler de entrada** estágio.  
  
 **Sombreador de vértice**  
 O estágio de sombreador de vértice processa vértices, normalmente executar operações como transformação, a estrutura e de iluminação. Sombreadores de vértices produzem o mesmo número de vértices que eles usa como entrada.  
  
 Na janela estágios de Pipeline, a saída do sombreador de vértice é visualizada como uma imagem de varredura de wireframe. Para fazer uma análise detalhada de resultados, selecione **sombreador de vértice** no **estágios de Pipeline gráficos** windows para exibir os vértices processados no Editor de imagem.  
  
> [!NOTE]
>  Se o `POSITION` ou `SV_POSITION` semântica não está presente na saída do sombreador de vértice e, em seguida, nada é exibido no **sombreador de vértice** estágio.  
  
 **Sombreador de envoltória** (Direct3D 11 e Direct3D 12 somente)  
 Os processos de estágio de sombreador de envoltória pontos que definem uma superfície de ordem inferior como uma linha, triângulo ou quad de controle. Como saída produz um patch de geometria de ordem superior e constantes do patch que são passados para o estágio de mosaico de função fixa.  
  
 O estágio de sombreador de envoltória não é visualizado na janela estágios de Pipeline.  
  
 **Estágio de tessellator** (Direct3D 11 e Direct3D 12 somente)  
 O estágio de tessellator é uma unidade de hardware de função fixa (não programável) que pré-processa o domínio representado pela saída do sombreador de envoltória. Como resultado, ele cria um padrão de amostragem do domínio e um conjunto de primitivos menores — pontos, linhas ou triângulos — que se conectam a esses exemplos.  
  
 O estágio de tessellator não é visualizado na janela estágios de Pipeline.  
  
 **Sombreador de domínio** (Direct3D 11 e Direct3D 12 somente)  
 O estágio de sombreador de domínio processa patches de geometria de ordem superior do sombreador de envoltório, fatores de subdivisão juntos no estágio de mosaico. O mosaico podem ser fatores incluem fatores de entrada tessellator, bem como fatores de saída. Como resultado, ele calcula a posição de vértice de um ponto em que o patch de saída de acordo com os fatores de tessellator.  
  
 O estágio de sombreador de domínio não é visualizado na janela estágios de Pipeline.  
  
 **Sombreador de geometria**  
 O estágio de sombreador geometria processa todos primitivos — pontos, linhas ou triângulos — junto com dados de vértice opcional para primitivos adjacentes de borda. Diferentemente de sombreadores de vértices sombreadores de geometria podem produzir mais ou menos primitivos que eles aceitam como entrada.  
  
 Na janela estágios de Pipeline, a saída do sombreador geometry é visualizada como uma imagem de varredura de wireframe. Para fazer uma análise detalhada de resultados, selecione **Geometry Shader** no **estágios de Pipeline gráficos** janela para exibir os primitivos processados no Editor de imagem.  
  
 **Estágio de saída do fluxo**  
 O estágio de saída de fluxo pode interceptar primitivos transformados antes da rasterização e gravá-las em memória. de lá os dados podem ser recirculated como entrada para anteriores estágios do pipeline de gráficos ou ser lidos por CPU.  
  
 O estágio de saída do fluxo não é visualizado na janela estágios de Pipeline.  
  
 **Estágio de rasterizador**  
 O estágio de rasterizador é uma unidade de hardware (não programável) de função fixa que converte os primitivos de vetor — pontos, linhas ou triângulos — em uma imagem de varredura por linha de verificação de conversão. Durante a rasterização vértices são transformados no espaço do clipe homogêneo e cortados. Como resultado, sombreadores de pixel são mapeados e atributos por vértice são interpolados entre o primitivo e prontas para o sombreador de pixel.  
  
 O estágio de rasterizador não é visualizado na janela estágios de Pipeline.  
  
 **Sombreador de pixel**  
 Os pixel shader estágio processos rasterizado primitivos junto com dados de vértice interpolada para gerar por pixel valores, como cor e profundidade.  
  
 Na janela estágios de Pipeline, a saída do sombreador de pixel é visualizada como uma imagem de varredura colorida. Para fazer uma análise detalhada de resultados, selecione **sombreador de Pixel** no **estágios de Pipeline gráficos** janela para exibir os primitivos processados no Editor de imagem.  
  
 **Fusão de saída**  
 O estágio de fusão saída combina o efeito de pixels recentemente renderizado junto com o conteúdo existente de seus buffers correspondentes, cores, profundidade e estêncil — para produzir novos valores nesses buffers.  
  
 Na janela estágios de Pipeline, a saída de fusão de saída é visualizada como uma imagem de varredura colorida. Para analisar mais detalhadamente os resultados, selecione **fusão de saída** no **estágios de Pipeline gráficos** janela para exibir o framebuffer mesclada.  
  
### <a name="vertex-and-geometry-shader-preview"></a>Vértices e visualização do sombreador de geometria  
 Quando você seleciona o estágio de sombreador de vértice ou geometria no **estágios do Pipeline** janela, você pode exibir as entradas e saídas de sombreador no painel abaixo.  Aqui, você encontrará os detalhes sobre a lista de vértices fornecido para os sombreadores depois que eles foram reunidos pelo estágio do assembler de entrada.  

 ![O Visualizador de buffer de entrada de estágio de sombreador de vértice](media/gfx_diag_vertex_shader_inbuffers.png)  
  
 Para exibir o resultado do estágio de sombreador de vértice, escolha a miniatura de estágio de sombreador de vértice para exibir um wireframe rasterizado em tamanho normal, da malha após seu foram transformados pelo sombreador de vértice.  
  
 ![A visualização de resultado do estágio de sombreador vértice](media/gfx_diag_vertex_shader_preview.png)  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: Objetos ausentes devido ao sombreamento de vértice](walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Passo a passo: depurando erros de renderização devido ao sombreamento](walkthrough-debugging-rendering-errors-due-to-shading.md)