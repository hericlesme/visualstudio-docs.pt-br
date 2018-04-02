---
title: Analisar erros de teste de carga usando o painel de contadores no Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- Load Test Analyzer, counters panel
ms.assetid: 981b4f1e-505a-4078-a06d-58ae17d996b4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 055925fd626e03df6e80fe02647fc2c1ca67d6ad
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-analyze-errors-using-the-counters-panel"></a>Como analisar erros usando o painel Contadores

O painel Contadores permanece visível na exibição Gráficos e na exibição Tabelas do Analisador de Testes de Carga enquanto um teste de carga está em execução ou quando você está analisando o resultado de um teste de carga. Para obter mais informações, consulte [Analisar resultados de teste de carga na exibição de gráficos](../test/analyze-load-test-results-in-the-graphs-view.md), [Analisar erros e resultados de teste de carga na exibição de tabelas](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) e [Como acessar resultados de teste de carga para análise](../test/how-to-access-load-test-results-for-analysis.md).

 O nó **Erros** no painel Contadores contém todos os erros detectados durante o teste de carga. O nó Erros contém vários nós de erro da subcategoria que são específicos a diferentes tipos de erro. Por exemplo, **Exceções** e **Erros de HTTP**.

 ![Nó de erro do painel de contadores](../test/media/ltest_errornode.png "LTest_ErrorNode")

## <a name="to-analyze-errors-in-the-counters-panel"></a>Para analisar erros no painel Contadores

1.  Depois que um teste de carga terminar ou depois que você carregar um resultado do teste, na barra de ferramentas do Analisador de Teste de Carga, escolha **Gráficos** ou **Tabelas**.

     O painel **Contadores** é mostrado na exibição Gráficos ou na exibição Tabelas.

2.  Se o painel Contadores não estiver visível, escolha **Mostrar painel de contadores** na barra de ferramentas.

3.  Expanda **Erros** e selecione uma categoria ou uma subcategoria de erro que você deseja analisar.

4.  Clique com o botão direito do mouse no erro e selecione uma das seguintes opções:

    -   **Mostrar Contador no Gráfico**: na exibição Gráficos, o erro é adicionado e realçado no gráfico selecionado. Para obter mais informações, consulte [Como adicionar e excluir contadores em gráficos](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md).

    -   **Mostrar contador na legenda**: o erro é adicionado e selecionado na legenda. Para obter mais informações, consulte [Usando a legenda de exibição dos gráficos para analisar testes de carga](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

    -   **Adicionar Gráfico**:

    1.  A caixa de diálogo **Digite o nome do gráfico** é exibida.

    2.  Na caixa de texto **Nome do gráfico**, digite um nome para o novo gráfico e escolha **OK**.

    3.  (Opcional) Clique com o botão direito do mouse no erro novamente e selecione **Mostrar Contador no Gráfico**.

         Para obter mais informações, consulte [Como criar gráficos personalizados](../test/how-to-create-custom-graphs-in-load-test-results.md).

5.  (Opcional) Se você estiver analisando um erro em um resultado de teste de carga concluído, considere usar os recursos de zoom na exibição Gráficos. Para obter mais informações, consulte [Como ampliar uma região do gráfico](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

    > [!TIP]
    > Se qualquer erro for detectado durante a execução do teste de carga, um link intitulado "erros", incluindo o número de erros encontrados, estará presente na barra de status do Analisador de Testes de Carga. Você pode escolher o link para exibir todos os erros na tabela **Erros** da exibição Tabelas.

## <a name="see-also"></a>Consulte também

- [Usando o painel Contadores nas exibições de Gráficos e Tabelas](../test/counters-panel-in-load-test-analyzer.md)
- [Analisar resultados de teste de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)