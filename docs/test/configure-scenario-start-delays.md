---
title: Configurar atrasos de início de cenário para testes de carga no Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, scenarios, start delays
ms.assetid: 2f634fba-8dfa-4c7a-a8b9-be867b78d16a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 2802172d3ba959b489e5449351d40395abe712a6
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="configure-scenario-start-delays-in-load-tests"></a>Configurar atrasos de início de cenário em testes de carga

Usando o Editor de Teste de Carga e a janela Propriedades, especifique um atraso antes do início de um cenário em um teste de carga.

Por exemplo, talvez você queira usar a propriedade **Atrasar tempo de início** se precisar que um cenário comece a produzir itens consumidos por outro cenário. Você pode atrasar o cenário de consumo para habilitar o cenário de produção a fim de popular alguns dados.

Outro exemplo é que você talvez tenha um cenário executado apenas em uma determinada hora do dia. Assim, você deseja atrasar o início do cenário para simular isso.

## <a name="specifying-the-delay-start-time-of-a-scenario"></a>Especificando Atrasar Tempo de Início de um cenário

Você pode especificar um atraso antes do início de um cenário em um teste de carga usando o Editor de teste de carga para alterar a propriedade **Atrasar tempo de início** na janela Propriedades.

> [!NOTE]
> Para obter uma lista completa das propriedades de cenário de teste da carga e suas descrições, consulte [Propriedades do cenário de teste de carga](../test/load-test-scenario-properties.md).

 Um exemplo de situação em que você talvez queira usar a propriedade **Atrasar tempo de início** é quando precisa que um cenário comece a produzir itens consumidos por outro cenário. Você pode atrasar o cenário de consumo para habilitar o cenário de produção a fim de popular alguns dados.

 Outro exemplo é que você talvez tenha um cenário executado apenas em uma determinada hora do dia. Assim, você deseja atrasar o início do cenário para simular isso.

> [!NOTE]
> Para obter uma lista completa das propriedades das configurações da execução e suas descrições, consulte [Propriedades do cenário de teste de carga](../test/load-test-scenario-properties.md).

### <a name="to-specify-the-delay-start-time-for-a-scenario"></a>Para especificar Atrasar Tempo de Início de um cenário

1. Abra um teste de carga.

     O Editor de Testes de Carga é exibido. A árvore do teste de carga é exibida.

2. Na pasta **Cenários** das árvores de teste de carga, escolha o nó do cenário para o qual você deseja especificar o atraso de tempo de início.

3. No menu **Exibir**, selecione **Janela de Propriedades**.

     As categorias e as propriedades do cenário são exibidas na janela Propriedades.

4. Na caixa de texto da propriedade **Atrasar tempo de início**, digite um valor temporal que indique o tempo de espera após o início do teste de carga, antes do início do cenário quando o teste de carga é executado.

    > [!NOTE]
    > Se o valor da propriedade **Desabilitar durante aquecimento** para o cenário for definido como **Verdadeiro**, o valor temporal das propriedades **Atrasar tempo de início** será aplicado após o período de aquecimento. Você pode controlar quais cenários estão incluídos no aquecimento usando a propriedade do cenário **Desabilitar durante aquecimento**.

5. Depois de alterar a propriedade, escolha **Salvar** no menu **Arquivo**. Assim, você pode executar o teste de carga usando o novo valor de **Atrasar tempo de início**.

## <a name="enabling-and-disabling-whether-a-scenario-runs-during-the-warm-up-period"></a>Habilitando e desabilitando se um cenário é executado durante o período de aquecimento

A propriedade **Desabilitar durante Aquecimento** é definida usando a janela Propriedades. A edição das propriedades do cenário de teste da carga é definida pelo Editor de testes de carga.

 A propriedade **Desabilitar durante aquecimento** é usada para indicar se o cenário deve ou não ser executado durante o período de aquecimento especificado na propriedade **Atrasar tempo de início**. Para obter mais informações, examine o procedimento anterior [Especificando Atrasar tempo de início em um cenário](../test/configure-scenario-start-delays.md#ConfiguringScenarioStartDelayHowTo).

> [!NOTE]
> Para obter uma lista completa das propriedades das configurações da execução e suas descrições, consulte [Propriedades do cenário de teste de carga](../test/load-test-scenario-properties.md).

### <a name="to-enable-or-disable-the-warm-up-period-for-a-scenario"></a>Para habilitar ou desabilitar o período de aquecimento para um cenário

1. Abra um teste de carga.

     O **Editor de Teste de Carga** é exibido. A árvore do teste de carga é exibida.

2. Na pasta **Cenários** das árvores de teste de carga, escolha o nó do cenário para o qual você deseja especificar os agentes a serem usados.

3. No menu **Exibir**, selecione **Janela de Propriedades**.

     As categorias e as propriedades do cenário são exibidas na janela Propriedades.

     Na propriedade **Desabilitar durante aquecimento**, selecione **Verdadeiro** ou **Falso**.

4. Depois de alterar a propriedade, escolha **Salvar** no menu **Arquivo**. Assim, você pode executar o teste de carga usando o novo valor de **Desabilitar durante aquecimento**.

## <a name="see-also"></a>Consulte também

- [Editando cenários de teste de carga](../test/edit-load-test-scenarios.md)
- [Configurar controladores e agentes de teste para testes de carga](../test/configure-test-agents-and-controllers-for-load-tests.md)
- [Propriedades do cenário de teste de carga](../test/load-test-scenario-properties.md)