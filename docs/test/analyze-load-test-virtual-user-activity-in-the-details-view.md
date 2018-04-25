---
title: Analisando a atividade do usuário virtual do teste de carga no Visual Studio | Microsoft Docs
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.activitychart
helpviewer_keywords:
- virtual user activity chart
- load test, virtual user activity chart
ms.assetid: 63f4bd42-3cfb-4eee-af68-e8334976539e
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 5f874b070e726374a20e821508115b5798f40b80
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Analisando a atividade de usuário virtual do teste de carga na exibição Detalhes do Analisador de Teste de Carga

**Gráfico de atividade do usuário virtual**

 ![Gráfico de atividade do usuário virtual](../test/media/virtual_actchart.png "Virtual_ActChart")

 A exibição Detalhes mostra o Gráfico de Atividade de Usuário Virtual, que é usado para analisar visualmente o que os usuários virtuais individuais fizeram durante o teste de carga. O Gráfico de Atividade de Usuário Virtual permite ver os padrões de atividade do usuário, os padrões de carga, a correlação de testes reprovados ou lentos, bem como as solicitações com outra atividade de usuário virtual. O Gráfico de Atividade de Usuário Virtual também pode ajudar a determinar picos de uso da CPU, quedas em solicitações por segundo e quais testes ou páginas estavam em execução durante os picos e as quedas.

> [!NOTE]
> Antes de executar o teste de carga no qual desejar usar o Gráfico de detalhes de atividade do usuário virtual, você precisa verificar se a propriedade **Armazenamento de detalhes de medição de tempo** está definida como **AllIndividualDetails** usando o Editor de Teste de Desempenho de Carga. Para obter mais informações, consulte [Como configurar a coleta de detalhes completos para habilitar o gráfico de atividade de usuário virtual](../test/how-to-configure-load-tests-to-collect-full-details.md).

 **Painel de legenda de detalhes**

 ![Painel de legenda de detalhes](../test/media/ltest_detailslegend.png "LTest_DetailsLegend")

 O painel de legenda de detalhes está visível no Gráfico de Atividade de Usuário Virtual. O painel permite filtrar testes, páginas e transações com base em vários critérios diferentes. Por exemplo, você pode remover alguns testes da exibição, ou remover todos os testes com êxito, ou remover testes reprovados com determinadas falhas. Também é possível remover todos os testes que não possuem logs.

 Você pode realçar testes que falharam, o que exibe todos os testes com falha em vermelho. Também é possível realçar testes que possuem logs de teste. Os testes com logs serão coloridos de verde.

 **Painel Filtrar resultados**

 ![Painel Filtrar resultados](../test/media/ltest_filterresults.png "LTest_FilterResults")

 O painel Resultados do filtro está visível no Gráfico de Atividade de Usuário Virtual. Esse painel pode filtrar o seguinte:

-   **Mostrar apenas os resultados com logs** Exibe apenas resultados de teste com logs de teste associados.

-   **Mostrar resultados bem-sucedidos** Exibe resultados bem-sucedidos.

-   **Mostrar resultados com erros** Exibe resultados com erros que podem ajudar na depuração.

## <a name="tasks"></a>Tarefas

|Tarefas|Tópicos associados|
|-----------|-----------------------|
|**Configurar o teste de carga para usar o Gráfico de atividade do usuário virtual:** antes de executar um teste de carga no qual deseja exibir dados de atividade do usuário virtual, primeiro você precisa definir as configurações de propriedade dos testes de carga.|-   [Como configurar a coleta de detalhes completos para habilitar o gráfico de atividade de usuário virtual](../test/how-to-configure-load-tests-to-collect-full-details.md)|
|**Executar o teste de carga:** depois de criar um teste de carga e configurá-lo para permitir a coleta dos dados de atividade do usuário virtual, você deverá executar o teste até sua conclusão para exibir o Gráfico de atividade do usuário virtual.||
|**Exibir os resultados de testes de carga que contenham os dados de atividade do usuário virtual:** depois que o teste de carga tiver sido criado e configurado e sua execução estiver concluída, você poderá exibir os dados de atividade do usuário virtual usando o Gráfico de atividade de usuário virtual.|-   [Analisar resultados de teste de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [Como analisar o que usuários virtuais estão fazendo durante um teste de carga](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Isolar problemas de desempenho em testes de carga:** é possível usar o Gráfico de atividade do usuário virtual para ajudar a isolar problemas de desempenho no teste de carga.|-   [Passo a passo: usando o gráfico de atividade de usuário virtual para isolar problemas](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Consulte também

- [Analisar resultados de teste de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analyze Load Test Results and Errors in the Tables View](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) (Analisar resultados de teste de carga e erros na exibição de tabelas)