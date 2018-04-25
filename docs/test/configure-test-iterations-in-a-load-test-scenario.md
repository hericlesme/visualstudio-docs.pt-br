---
title: Configurando iterações de teste para testes de carga no Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios, iterations
- load test, iterations
- load tests, sceanrios
ms.assetid: ac480fb7-f4f7-47dc-9ae5-98be3aca4fba
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 6aac1f950bcfaf4c8308913d389d6fd3dec15c2d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="configure-test-iterations-in-a-load-test-scenario"></a>Configurar iterações de teste em um cenário de teste de carga

Para definir configurações de iteração de teste, edite um cenário de teste de carga usando o Editor de Teste de Carga e a janela Propriedades. Por padrão, um cenário de teste de carga é configurado sem especificar o número máximo de iterações de teste. Você tem a opção de configurar o número máximo de iterações no cenário e por quanto tempo pausar entre elas.

## <a name="specify-the-maximum-test-iterations-for-a-scenario"></a>Especificar o máximo de iterações de teste para um cenário

Você pode especificar o número máximo de vezes que deseja que os testes sejam executados para um cenário usando o Editor de teste de carga para alterar a propriedade de **Número máximo de iterações de teste** na janela Propriedades.

A propriedade de **Número máximo de iterações de teste** controla o número máximo de iterações de teste para execução no cenário. Assim como na propriedade **Iterações de teste** das configurações de execução de teste de carga, esse é o máximo entre todos os usuários em todos os agentes, não por configuração de usuário.

> [!NOTE]
> Para obter uma lista completa das propriedades de cenário de teste da carga e suas descrições, consulte [Propriedades do cenário de teste de carga](../test/load-test-scenario-properties.md).

 Para a combinação de testes sequenciais, uma iteração é uma passagem por todos os testes na combinação. Para todas as outras combinações de testes, cada execução de teste conta como uma iteração. Para obter mais informações, consulte [Sobre o controle misto](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).

 Se o teste de carga for um teste de carga baseado em duração, e a duração expirar antes que a contagem de iterações seja concluída, o teste ainda será parado. Se o teste for baseado em iteração, e as iterações de teste forem atendidas antes das iterações do cenário, o teste será parado. A duração é configurada usando a propriedade de **Duração da execução** na janela Propriedades associadas a uma configuração de execução em um teste de carga.

 Quando a contagem de iterações do cenário for atingida, a execução do cenário será interrompida, mas todos os outros cenários ativos continuarão a ser executados.

> [!NOTE]
> Uma propriedade relacionada é a propriedade **Exclusivo** em uma fonte de dados de teste na Web, que se move em sequência pelos dados, linha por linha, mas apenas uma vez para cada registro. Para obter mais informações, consulte [Adicionar uma fonte de dados a um teste de desempenho Web](../test/add-a-data-source-to-a-web-performance-test.md).

 A propriedade de **Número máximo de iterações de teste** é útil para diversas situações. Alguns testadores de carga preferem executar testes baseados em iteração, enquanto outros preferem executar testes baseados em duração.

 ![Especificando iterações de teste em um cenário](../test/media/loadtest_prop.png "LoadTest_Prop")

### <a name="to-specify-the-maximum-test-iterations"></a>Para especificar o máximo de iterações de teste

1.  Abra um teste de carga.

2.  O Editor de Testes de Carga é exibido. A árvore do teste de carga é exibida.

3.  Na pasta **Cenários** das árvores de teste de carga, escolha o nó do cenário para o qual você deseja especificar o número máximo de iterações de teste.

4.  No menu **Exibir**, selecione **Janela de Propriedades**.

     As categorias e as propriedades do cenário são exibidas na janela Propriedades.

5.  Na caixa de texto da propriedade de **Número máximo de iterações de teste**, digite um valor que indique o número máximo de testes para executar no cenário quando o teste de carga for executado.

    > [!NOTE]
    > Usar um valor de 0 para a propriedade de **Número máximo de iterações de teste** não especifica nenhuma iteração máxima.

6.  Depois de alterar a propriedade, escolha **Salvar** no menu **Arquivo**. Assim, você pode executar o teste de carga usando o novo valor de **Número máximo de iterações de teste**.

## <a name="specifying-think-times-between-test-iterations-for-a-scenario"></a>Especificando tempos de processamento entre iterações de teste para um cenário

A propriedade de **Tempo de processamento entre iterações de teste** é definida usando a janela Propriedades para editar as propriedades do cenário de teste de carga no Editor de Teste de Carga.

A propriedade de **Tempo de processamento entre iterações de teste** é usada para especificar quantos segundos esperar antes de iniciar uma iteração de teste.

> [!NOTE]
> Para obter uma lista completa das propriedades de cenário de teste da carga e suas descrições, consulte [Propriedades do cenário de teste de carga](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-think-times-between-test-iterations"></a>Para especificar os tempos de processamento entre iterações de teste

1.  Abra um teste de carga.

     O **Editor de Teste de Carga** é exibido. A árvore do teste de carga é exibida.

2.  Na pasta **Cenários** das árvores de teste de carga, escolha o nó do cenário para o qual deseja especificar os agentes a serem usados.

3.  No menu **Exibir**, selecione **Janela de Propriedades**.

     As categorias e as propriedades do cenário são exibidas na janela Propriedades.

4.  O valor da propriedade **Tempo de processamento entre iterações de teste**, digite um número que represente os segundos a esperar antes de começar a próxima iteração de teste.

5.  Depois de alterar a propriedade, escolha **Salvar** no menu **Arquivo**. Assim, você pode executar o teste de carga usando o novo valor de **Tempo de processamento entre iterações de teste**.

## <a name="see-also"></a>Consulte também

- [Editando cenários de teste de carga](../test/edit-load-test-scenarios.md)
- [Configurar controladores e agentes de teste para testes de carga](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Propriedades do cenário de teste de carga](../test/load-test-scenario-properties.md)
- [Editando tempos de processamento para simular atrasos de interação humana do site](../test/edit-think-times-in-load-test-scenarios.md)