---
title: Ampliar gráficos de resultados do teste de carga no Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.graphzoom
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, zooming with graphs
ms.assetid: 729b4c30-4bc3-4698-91b3-17a676897443
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 9e2379161051c821af07b6da5b102177178a0d7f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results"></a>Como ampliar uma região do gráfico em resultados de teste de carga

Após a conclusão de um teste de carga, você poderá usar as barras de zoom para ampliar e rolar para uma região do gráfico. Ao ampliar, você pode examinar detalhadamente os dados que foram gerados durante uma execução de teste de carga.

> [!NOTE]
> A ampliação estará disponível somente quando você estiver analisando o resultado de um teste de carga concluído, não enquanto você estiver observando os resultados de um teste em execução.

 O controle de zoom fica visível apenas no Analisador de Testes de Carga quando você exibe um resultado de teste de carga no modo de zoom. O modo de zoom será estabelecido na Exibição de gráfico quando um teste de carga for concluído ou um teste de carga que foi executado anteriormente for carregado. Você pode mostrar ou ocultar os controles de zoom nos gráficos usando Mostrar Controles de Zoom na barra de ferramentas.

 O zoom do eixo x horizontal pode ser ajustado para analisar os períodos de tempo específicos durante o teste de carga. O zoom do eixo y vertical pode ser ajustado para analisar intervalos de valores específicos dos contadores que são incluídos no gráfico.

 Os controles de zoom do intervalo de valores vertical e da linha do tempo horizontal podem ser ajustados usando o mouse. O controle de linha do tempo horizontal também pode ser ajustado usando as teclas de seta para a esquerda e para a direita. Usando as teclas de seta para ajustar o controle de zoom, você pode ajustar o intervalo de janelas em 1 intervalo de amostragem por vez. Usar as teclas SHIFT e de seta faz ajustes de 10 intervalos de amostragem.

 Para ajustar o controle de zoom usando a tecla de seta, primeiro defina o foco no controle de zoom usando a tecla TAB. Quando o controle deslizante esquerdo tiver o foco, as teclas de seta moverão o limite inicial da janela de zoom em 1 intervalo para a esquerda ou para a direita. Quando o foco estiver no controle deslizante central, você poderá usar as teclas de seta para rolar a janela de zoom para a esquerda ou para a direita 1 intervalo de amostragem sem alterar o tamanho da janela de zoom. E, por fim, o controle deslizante do lado direito é movido, estendendo ou reduzindo o intervalo do fim da janela de zoom em 1 intervalo de amostragem.

 Para retornar os controles de zoom horizontal e vertical para mostrar os intervalos de valores e linha do tempo completos, você pode usar a opção **Aplicar zoom horizontal**, a opção **Aplicar zoom vertical** ou a opção **Aplicar zoom para ambos** no menu pop-up do gráfico.

> [!TIP]
> É possível usar **Sincronizar controles de zoom horizontal** na barra de ferramentas para ativar ou desativar a sincronização de zoom horizontal automática. Com a sincronização ativada, qualquer zoom que você aplicar a um gráfico também será aplicado a qualquer outro gráfico na Exibição de Gráficos.

 ![Controle de zoom de exibição de gráfico](../test/media/ltest_zoomcontrol.png "LTest_ZoomControl") Controle de zoom de exibição de gráfico

 Na ilustração anterior, foi aplicado zoom no gráfico Sistema em Teste para investigação de problemas de limite. As violações de limite foram habilitadas usando **Mostrar violações de limite no gráfico** no menu suspenso **Opções de gráfico** na barra de ferramentas.

 Para obter mais informações, consulte [Analisar resultados de teste de carga na exibição de gráficos](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="displaying-graphs"></a>Exibindo gráficos
 Antes de modificar a exibição de um gráfico ampliando ou reduzindo, ou rolando, siga este procedimento para exibir gráficos.

### <a name="to-display-graphs"></a>Para exibir gráficos

1.  Execute um teste de carga até que ele seja todo concluído.

2.  Ao fim da execução de teste de carga, escolha **Sim** na caixa de diálogo que pergunta sobre exibir resultados do repositório de resultados de testes de carga.

     \- ou -

     Exiba os detalhes de um teste de carga executado anteriormente. Para obter mais informações, consulte [Como acessar resultados de teste de carga para análise](../test/how-to-access-load-test-results-for-analysis.md).

3.  Escolha **Gráficos** se os gráficos não forem exibidos.

4.  Se as barras de zoom não forem exibidas, escolha **Mostrar controles de zoom**.

     Duas barras de zoom são disponibilizadas para cada gráfico. A barra de zoom que controla a escala vertical é exibida à esquerda do gráfico. A barra de zoom que controla a escala horizontal é exibida abaixo do gráfico.

     Cada barra de zoom tem duas alças. Uma alça é uma área retangular em cada extremidade da barra de zoom.

## <a name="zooming-and-scrolling"></a>Ampliação e rolagem
 Quando vários gráficos forem exibidos, você poderá mantê-los sincronizados para que exibam a mesma parte da execução de teste de carga.

### <a name="to-synchronize-zooming-and-scrolling"></a>Para sincronizar a ampliação e a rolagem

1.  No Analisador de Teste de Carga, escolha **Sincronizar controles de zoom horizontal**.

     Quando o botão Sincronizar Controles de Zoom Horizontal for selecionado, a ampliação e a rolagem da escala de tempo de um gráfico individual também vai ampliar e rolar a escala de tempo dos outros gráficos.

2.  Novamente, escolha Sincronizar Controles de Zoom Horizontal.

     Quando o botão Sincronizar Controles de Zoom Horizontal não for selecionado, a ampliação e a rolagem da escala de tempo de um gráfico individual afetará apenas esse gráfico.

### <a name="to-zoom-and-scroll-to-a-region-of-the-graph"></a>Para ampliar e rolar para uma região do gráfico

1.  Na barra de zoom abaixo de um gráfico, arraste a alça do lado esquerdo para a direita.

     Isso amplia a última parte da execução de teste. Da mesma forma, arrastar a alça do lado direito para a esquerda amplia as partes anteriores da execução de teste.

2.  Para ampliar uma determinada área, deslize ambas as alças para o centro de um gráfico.

     Quanto mais próximas as duas alças estiverem uma da outra, mais você amplia para exibir segmentos mais curtos e finos do teste de carga.

     Escolha a seção central da barra de zoom e arraste-a para rolar até um determinado ponto do teste de carga.

### <a name="to-zoom-to-a-region-of-the-graph-by-choosing-and-dragging"></a>Para ampliar uma região do gráfico escolhendo e arrastando

1.  Escolha um gráfico em uma extremidade da área de zoom.

2.  Arraste o ponteiro do mouse para a outra extremidade da área de zoom.

3.  Solte o botão do mouse.

     Isso aumenta a área que você definiu escolhendo e arrastando.

 O procedimento a seguir descreve como reduzir rapidamente sem precisar ajustar as extremidades da barra de zoom.

### <a name="to-zoom-out"></a>Para reduzir

1.  Clique com o botão direito do mouse em um gráfico ampliado.

2.  No menu de atalho, selecione **Aplicar zoom horizontal**.

     Isso reduz para mostrar a duração inteira da execução de teste de carga.

## <a name="see-also"></a>Consulte também

- [Analisar resultados de teste de carga na exibição de gráficos](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analisar resultados de teste de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Como adicionar e excluir contadores em gráficos](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)