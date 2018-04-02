---
title: Opções de plotagem para gráficos de contadores de testes de carga no Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, graphing counters
ms.assetid: 1969c20b-e0eb-48f6-a49f-a9090cd86008
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 00860a262573491a358c0f992577f48fc3480d93
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-specify-plot-options-for-graphing-counters"></a>Como especificar opções de plotagem para contadores de representação gráfica

A caixa de diálogo **Opções de Plotagem** permite alterar a cor e o estilo de linha de um contador plotado em um gráfico. Você também pode corrigir o intervalo em um valor específico ou definir o intervalo para ser ajustado automaticamente com base nos dados da amostra.

![Caixa de diálogo Opções de Plotagem](../test/media/ltest_plotoptions.png "LTest_PlotOptions")

## <a name="to-specify-plotting-options-for-graphs"></a>Para especificar opções de plotagem para gráficos

1.  No Analisador de Teste de Carga, escolha **Gráficos** na barra de ferramentas do teste de carga.

     Isso exibe os resultados do teste de carga na exibição de gráficos.

2.  Na legenda ou no gráfico, clique com o botão direito do mouse na linha de plotagem atual do contador de desempenho cuja opção de plotagem deseja alterar e selecione **Opções de Plotagem**.

     A caixa de diálogo **Opções de Plotagem** é exibida.

3.  Use a lista suspensa **Cor** e selecione a cor que deseja usar para plotar o contador de desempenho.

4.  Use a lista suspensa **Estilo** e selecione o estilo que deseja usar para plotar o contador de desempenho.

5.  Realize um dos seguintes procedimentos:

     Selecione **Ajustar automaticamente o intervalo** (padrão)

     \- ou -

     Desmarque **Ajustar automaticamente o intervalo** e use a lista suspensa **Intervalo** para especificar o intervalo que deseja usar na plotagem do contador de desempenho.

6.  Escolha **OK**.

     O contador de desempenho cujas opções você alterou é exibido no gráfico com as alterações que você especificou.

## <a name="see-also"></a>Consulte também

- [Analisar resultados de teste de carga na exibição de gráficos](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Como criar gráficos personalizados](../test/how-to-create-custom-graphs-in-load-test-results.md)
- [Analisar resultados de teste de carga na exibição de gráficos](../test/analyze-load-test-results-in-the-graphs-view.md)