---
title: Painel Contadores para analisar teste de carga no Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, counters panel
ms.assetid: e1a388d7-5d33-4631-931a-5653ac4aefdc
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 9e693872784519f5cdcacbd0691b6f69334af22e
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="use-the-counters-panel-in-graphs-view-and-tables-view"></a>Usar o painel Contadores nas exibições de Gráficos e Tabelas

O painel Contadores permanece visível na exibição Gráficos e na exibição Tabelas do Analisador de Testes de Carga enquanto um teste de carga está em execução ou quando você está analisando o resultado de um teste de carga. Para obter mais informações, consulte [Analisar resultados de teste de carga na exibição de gráficos](../test/analyze-load-test-results-in-the-graphs-view.md), [Analisar erros e resultados de teste de carga na exibição de tabelas](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) e [Como acessar resultados de teste de carga para análise](../test/how-to-access-load-test-results-for-analysis.md).

O painel Contadores mostra uma exibição estruturada de todos os contadores de desempenho que foram coletados durante o teste de carga. Você pode mostrar ou ocultar o painel de contadores escolhendo **Mostrar painel de contadores** na barra de ferramentas do Analisador de Teste de Carga.

Os contadores são organizados em uma estrutura de árvore, onde os nós folha são as instâncias de contador de desempenho que podem ser representadas graficamente.

O painel Contadores fornece os seguintes recursos:

-   Comunica informações de violação de limite.

-   Seleção dos contadores para representação gráfica.

-   Uma exibição de árvore estruturada de todos os contadores de desempenho coletados durante a execução de teste de carga com as seguintes ramificações principais:

    -   **Geral:** contém o resumo dos dados de contador de desempenho para cada agente de teste e para o teste de carga inteiro.

    -   **Nome do Cenário:** as ramificações rotuladas com nomes de cenário do teste de carga na árvore de contador de desempenho contêm todas as instâncias de contador de teste de carga associadas a um cenário de teste de carga específico. A maioria dos contadores de teste de carga é aninhada em uma ramificação de cenário.

         Uma ramificação de cenário contém nós de teste de desempenho na Web. Os nós de teste de desempenho na Web contêm nós de Páginas, Solicitações e Transação. Qualquer nó folha nessa estrutura é um contador de desempenho que pode ser adicionado a um gráfico.

    -   **Computadores:** contém todas as instâncias de não contador de teste de carga agrupadas por computador. A ramificação Computadores contém um nó para cada computador associado ao controlador de teste de carga especificado na seção Funções das configurações de teste selecionadas no momento. Para obter mais informações, consulte [Controladores e agentes de teste](configure-test-agents-and-controllers-for-load-tests.md).

         Cada nó de computador contém um conjunto de categorias de contador de desempenho coletadas no computador em questão. As categorias contêm contadores e os contadores contêm nomes de instância de contador de desempenho.

    -   **Erros:** contém todos os erros detectados durante o teste de carga. O nó Erros contém várias subcategorias de nós de erro. As subcategorias são específicas para diferentes tipos de erros, por exemplo, exceções e erros de HTTP.

### <a name="scenario-name-node-in-counters-panel"></a>Nó Nome do cenário no painel Contadores

|||
|-|-|
|![Nó de nome do cenário no painel do contador](../test/media/ltest__namenode.png)|1. Todos os contadores de desempenho associados ao Scenario1 do teste de carga aparecem nesse nó.<br />2. Todos os testes de um cenário são localizados embaixo do nó do cenário. O rótulo indica o nome do teste.<br />3. Os nós folha em um nó de teste são os contadores de caso de teste de carga em que o nome da instância do contador é o nome do teste.<br />4. Todas as instâncias de contador de página de teste de carga associadas a uma ramificação de teste de desempenho na Web. Nesse nó, todas as instâncias de contador de ritmo do teste de carga associadas à página Login GET (Nome do relatório) do teste de desempenho na Web IBuyBrowse no Scenario1 do teste de carga são contidas aqui.<br />5. Os nós folha sob um nó de página são contadores de página de teste de carga.<br />6. Todas as instâncias de contador de solicitações do teste de carga associadas a um teste de desempenho na Web são contidas em uma ramificação de teste de desempenho na Web. Nesse nó, todas as instâncias de contador de solicitação associadas à solicitação Login GET (Nome do relatório) do teste de desempenho na Web IBuyBrowse no Scenario1 do teste de carga são contidas aqui.<br />7. Os nós folha sob um nó de solicitação são contadores de solicitação de teste de carga.<br />8. Todas as instâncias de contador de transação do teste de carga associadas a um teste de desempenho na Web são contidas em uma ramificação de teste de desempenho na Web. Nesse nó, todas as instâncias de contador de transação associadas à transação denominada Transaction1 do teste de desempenho na Web IBuyBrowse no Scenario1 do teste de carga são contidas aqui.<br />9. Os nós folha sob um nó de transação são contadores de transação de teste de carga.<br />10. Nó Teste de unidade.|

## <a name="tasks"></a>Tarefas

|Tarefas|Tópicos associados|
|-----------|-----------------------|
|**Adicionar mais contadores de desempenho a um gráfico na exibição de gráfico:** no painel Contadores, você pode adicionar tipos diferentes de dados a um gráfico de teste de carga adicionando mais contadores de desempenho no gráfico.|-   [Como adicionar e excluir contadores em gráficos](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)|
|**Analisar os limites especificados no teste de carga que foram violados:** o painel Contadores mostra ícones que representam as violações de limite que você pode adicionar a tabelas e gráficos para análise posterior.|-   [Como analisar violações de limite usando o painel Contadores](../test/analyze-threshold-rule-violations-in-load-tests.md)|
|**Analisar os erros detectados durante a execução de teste de carga:** o painel Contadores inclui um nó de erros que contém categorias e subcategorias de erro, como erros de HTTP, que você pode usar para adicionar erros a gráficos para análise posterior.|-   [Como analisar erros usando o painel Contadores](../test/how-to-analyze-errors-using-the-counters-panel.md)|

## <a name="performance-counter-sampling-interval-considerations"></a>Considerações sobre o intervalo de amostragem do contador de desempenho

Escolha um valor para a propriedade **Taxa de Amostragem** nas configurações de execução de teste de carga com base na duração do seu teste de carga. Uma taxa de amostragem menor, como o valor padrão de cinco segundos, requer mais espaço no banco de dados dos resultados de testes de carga. Para testes de carga mais longos, aumentar a taxa de amostragem reduzirá a quantidade de dados coletados. Para obter mais informações, consulte [Como especificar a taxa de amostragem](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Veja algumas diretrizes para taxas de amostragem:

|Duração do teste de carga|Taxa de amostragem recomendada|
|------------------------|-----------------------------|
|\< 1 hora|5 segundos|
|1 a 8 horas|15 segundos|
|8 a 24 horas|30 segundos|
|> 24 horas|60 segundos|

## <a name="considerations-for-including-timing-details-to-collect-percentile-data"></a>Considerações para inclusão de detalhes de medição de tempo para coletar dados de percentil

Há uma propriedade nas configurações de execução no Editor de Teste de Carga denominada **Armazenamento de detalhes de medição de tempo**. Se a propriedade **Armazenamento de Detalhes de Medição de Tempo** estiver habilitada, o tempo para execução de cada teste, transação e página individual durante o teste de carga será armazenado no repositório de resultados de testes de carga. Isso permite que os 90º e 95º dados de percentil sejam mostrados nas tabelas Testes, Transações e Páginas do Analisador de Testes de Carga.

Há duas opções para habilitar a propriedade **Armazenamento de detalhes de medição de tempo** nas propriedades de configurações de execução: **StatisticsOnly** e **AllIndividualDetails**. Seja qual opção for escolhidas, todos os testes, páginas e transações individuais são cronometrados, e os dados de percentil são calculados dos dados de medição de tempo individuais. A diferença é que, com a opção **StatisticsOnly**, assim que os dados de percentil são calculados, os dados de medição de tempo individuais são excluídos do repositório. Isso reduz a quantidade de espaço necessário no repositório quando você usa detalhes de medição de tempo. No entanto, os usuários avançados podem querer processar os dados detalhados de medição de tempo de outras formas, usando ferramentas SQL. Nesse caso, a opção **AllIndividualDetails** deve ser usada para que os dados detalhados de medição de tempo estejam disponíveis para esse processamento. Além disso, se você definir a propriedade para **AllIndividualDetails**, será possível analisar a atividade do usuário virtual usando o Gráfico de atividade do usuário virtual no Analisador de Teste de Carga após a conclusão da execução do teste de carga. Para obter mais informações, consulte [Analisando a atividade de usuário virtual na exibição Detalhes](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

A quantidade de espaço necessária no repositório de resultados de testes de carga para armazenar os dados detalhados de medição de tempo pode ser grande, especialmente para testes de carga mais longos. Além disso, o tempo para armazenar esses dados no repositório de resultados de testes de carga no final do teste de carga é mais longo, pois esses dados são armazenados nos agentes de teste de carga até que o teste de carga seja concluído. Quando o teste de carga é concluído, os dados são armazenados no repositório. Por padrão, a propriedade **Armazenamento de detalhes de medição de tempo** fica habilitada. Se isso for um problema para o seu ambiente de teste, talvez seja conveniente definir o **Armazenamento de detalhes de medição de tempo** como **Nenhum**.

Para obter mais informações, consulte [Como especificar a propriedade de armazenamento dos detalhes de intervalo](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

## <a name="see-also"></a>Consulte também

- [Analisar resultados de teste de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)