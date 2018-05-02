---
title: Usando o Gráfico de atividade de usuário virtual em testes de carga no Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual user activity chart
- virtual user activity chart, isolating performance issues
ms.assetid: d1c10fb9-cfeb-4e7f-9991-2d1e1103699e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: fedc9aebb4d57e258370179bbf820abdc8978940
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-using-the-virtual-user-activity-chart-to-isolate-issues"></a>Informações passo a passo: usando o gráfico de atividade de usuário virtual

Neste passo a passo, você aprenderá a usar o Gráfico de Atividade de Usuário Virtual para isolar os erros que ocorreram para os usuários virtuais individuais que executaram seu teste de carga.

 O Gráfico de Atividade de Usuário Virtual permite visualizar a atividade de usuário virtual que está associada ao teste de carga. Cada linha do gráfico representa um usuário virtual individual. O Gráfico de Atividade de Usuário Virtual mostra exatamente o que cada usuário virtual executou durante o teste. Isso permite isolar problemas de desempenho vendo padrões de atividade de usuário, padrões de carga, correlação de testes reprovados ou lentos, e ver as solicitações com outra atividade de usuário virtual. O Gráfico de Atividade de Usuário Virtual está disponível apenas depois da conclusão da execução do teste de carga.

 Nesta explicação passo a passo, você concluirá as seguintes tarefas:

-   Saiba como usar as seguintes ferramentas associadas ao Gráfico de Atividade de Usuário Virtual:

    -   Use a ferramenta **Zoom para o período de tempo** para especificar um período específico no gráfico que você deseja analisar.

    -   Use o painel **Legenda de detalhes** e o painel **Filtrar resultados** para aplicar a filtragem no gráfico e ajudar a isolar problemas.

-   Use o Gráfico de Atividade de Usuário Virtual para analisar um erro que ocorreu para um usuário específico virtual e ver os detalhes problemáticos do tipo de erro.

 Para obter mais informações, consulte [Analisando a atividade de usuário virtual na exibição Detalhes](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

## <a name="prerequisites"></a>Pré-requisitos

-   Visual Studio Enterprise

-   Complete esses procedimentos:

    -   [Gravar e executar um teste de desempenho Web](http://msdn.microsoft.com/en-us/bd0a82fd-cec0-4861-bc09-e1b0b2d258ef).

    -   [Criar e executar um teste de carga](http://msdn.microsoft.com/en-us/7041cbcf-9ab1-4579-98ff-8f296aeaded4)

## <a name="open-the-colorwebapp-solution-created-in-the-previous-walkthroughs"></a>Abrir a solução ColorWebApp criada nos passo a passo anteriores

### <a name="open-the-solution"></a>Abrir a solução

1.  Inicie o Visual Studio.

2.  Abra a solução ColorWebApp que contém o LoadTest1.loadtest. Este teste de carga é resultado da execução das etapas nas três explicações passo a passo listadas no início deste tópico na seção de pré-requisitos.

     As etapas restantes deste passo a passo presumem um aplicativo Web denominado ColorWebApp, um teste de desempenho na Web chamado ColorWebAppTest.webtest e um teste de carga chamado LoadTest1.loadtest.

## <a name="run-the-load-test"></a>Executar o teste de carga
 Execute o teste de carga para coletar dados da atividade de usuário virtual.

### <a name="run-the-load-test-to-collect-virtual-user-activity-data"></a>Executar o teste de carga para coletar dados da atividade de usuário virtual

-   No Editor de Teste de Carga, escolha o botão **Executar** na barra de ferramentas. A execução de LoadTest1 iniciará.

## <a name="isolate-issues-in-the-virtual-user-activity-chart"></a>Isolar problemas no Gráfico de Atividade de Usuário Virtual

Após a execução do teste de carga e a coleta dos dados de atividade de usuário virtual, você pode ver os dados nos resultados do teste de carga usando a exibição Detalhes do Analisador de Testes de Carga no Gráfico de Atividade de Usuário Virtual. Além disso, você pode usar o Gráfico de Atividade de Usuário Virtual para ajudar a isolar problemas de desempenho no teste de carga.

### <a name="to-use-the-virtual-user-activity-chart-in-your-load-test-results"></a>Para usar o Gráfico de Atividade de Usuário Virtual nos resultados do teste de carga

1.  Depois que a execução do teste de carga termina, a página Resumo para os resultados do teste de carga é exibida no Analisador de Testes de Carga. Escolha o botão **Gráficos** na barra de ferramentas.

     A exibição Gráficos será mostrada.

2.  No gráfico **Tempo de Resposta de Página**, clique com o botão direito do mouse em um dos ícones de violação de limite e selecione **Ir para detalhe do usuário**.

    > [!NOTE]
    > Também é possível usar o botão **Detalhes** na barra de ferramentas do Editor de Teste de Carga para abrir o Gráfico de atividade do usuário. No entanto, se você usar a opção **Ir para detalhe do usuário**, o Gráfico de atividade do usuário virtual ampliará automaticamente a parte do teste em que você clicou com o botão direito do mouse.

     A exibição Detalhes é exibida com o **Gráfico de atividade do usuário virtual** focado no período em que as violações de limite ocorreram.

     No eixo y, os traços horizontais representam usuários virtuais individuais. O eixo x exibe a linha do tempo da execução do teste de carga.

3.  Na ferramenta **Zoom para o período de tempo** abaixo do **Gráfico de atividade do usuário virtual**, ajuste os controles deslizantes à esquerda e à direita até que ambos estejam próximos ao ícone de violação de limite. Isso altera a escala de tempo no **Gráfico de atividade do usuário virtual**

4.  Na **Legenda de detalhes**, marque a caixa de seleção **(Realçar de erros)**. Observe que o usuário virtual que causou a violação de limite está realçado.

5.  No painel **Filtrar resultados**, desmarque as caixas de seleção **Mostrar resultados bem-sucedidos** e **HttpError**, mas deixe a caixa de seleção **ValidationRuleError** marcada.

     O **Gráfico de atividade do usuário virtual** exibe apenas os usuários virtuais que passaram mais de 3 segundos na página Red.aspx, conforme especificado pela violação de limite configurada no passo a passo anterior.

6.  Coloque o ponteiro do mouse na linha horizontal que representa o usuário virtual com o erro da regra de validação da violação de limite.

7.  Uma dica de ferramenta é exibida com as seguintes informações:

    -   **ID de usuário**

    -   **Cenário**

    -   **Teste**

    -   **Resultado**

    -   **Network**

    -   **Hora de início**

    -   **Duração**

    -   **Agente**

    -   **Log de teste**

8.  Observe que **Log de teste** é um link. Escolha o link **Log de teste**.

9. O teste de desempenho na Web ColorWebTest que é associado ao log é aberto no Visualizador de Resultados de Testes na Web. Isso permite isolar onde as violações de limite ocorreram.

     É possível usar várias configurações nos painéis **Legenda de detalhes** e **Filtrar resultados** para ajudar a isolar problemas de desempenho e erros nos testes de carga. Experimente essas configurações e a ferramenta **Zoom para o período de tempo** para ver como os dados do usuário virtual são apresentados no **Gráfico de atividade do usuário virtual**.

## <a name="see-also"></a>Consulte também

- [Analisando a atividade de usuário virtual na exibição Detalhes](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Controladores e agentes de teste](configure-test-agents-and-controllers-for-load-tests.md)
- [Como criar uma configuração de teste para um teste de carga distribuída](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Instalar e configurar agentes de teste](../test/lab-management/install-configure-test-agents.md)
- [Coletar informações de diagnóstico usando configurações de teste](../test/collect-diagnostic-information-using-test-settings.md)