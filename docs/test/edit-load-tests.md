---
title: Editando testes de carga no Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- Load Test Editor
- load tests, Load Test Editor
ms.assetid: ba16ed02-137e-40bf-a4cb-45d87d922d37
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: f8a6d4bbec460103f1e8db596fa5d8b523c1bd92
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="edit-load-tests"></a>Editar testes de carga

Testes de carga executam testes de desempenho Web ou testes de unidade para simular muitos usuários acessando um servidor ao mesmo tempo. Um teste de carga fornece acesso a dados de estresse e desempenho do aplicativo. Um teste de carga pode ser configurado para emular várias condições de carga, como cargas e tipos de rede.

> [!NOTE]
> Testes de carga estão disponíveis somente na Enterprise Edition do Visual Studio 2017.

Um teste de carga é definido por *cenários*, *conjuntos de contadores* e *configurações de execução*. A ilustração a seguir explica as diferenças entre [cenários](../test/edit-load-test-scenarios.md), [conjuntos de contadores](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md) e [configurações de execução](../test/load-test-run-settings-properties.md):

![Arquitetura de teste de carga](../test/media/load_test_editor.png)

## <a name="edit-load-test-scenario-settings"></a>Editar configurações de cenário de teste de carga

Um cenário é usado para modelar como um grupo de usuários interage com um aplicativo para servidores. Um cenário consiste em um padrão de carga, um modelo de combinação de testes, uma combinação de navegadores e de redes. Um teste de carga pode ter mais de um cenário, e um único cenário podem conter testes de desempenho na Web e testes de unidade. Agrupando configurações semelhantes, um cenário permite agrupar e executar testes de uma natureza semelhante.

Para obter mais informações, consulte [Editando cenários de teste de carga](../test/edit-load-test-scenarios.md) e [Propriedades de cenário de teste de carga](../test/load-test-scenario-properties.md).

## <a name="configure-and-manage-performance-counter-sets"></a>Configurar e gerenciar conjuntos de contadores de desempenho

Os testes de carga oferecem conjuntos de contadores nomeados, organizados por tecnologia, úteis para quando você analisar dados de contadores de desempenho. Os conjuntos de contadores incluem Teste de Carga, IIS, ASP.NET e SQL. Quando você cria um teste de carga com o Novo Assistente de Teste de Carga, um conjunto inicial de contadores predefinidos importantes é configurado para os computadores que você especifica para incluir no teste de carga. Você gerencia os contadores no Editor de testes de carga.

Para obter mais informações, consulte [Especificando os conjuntos de contadores e as regras de limite para computadores em um teste de carga](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="configure-and-manage-load-test-run-settings"></a>Definir e gerenciar configurações de execução de teste de carga

Configurações de execução são propriedades que influenciam a maneira como um teste de carga é executado. As configurações de execução são organizadas por categorias na janela Propriedades.

Para obter mais informações, consulte [Definindo configurações de execução de teste de carga](../test/configure-load-test-run-settings.md) e [Propriedades de configurações de execução de teste de carga](../test/load-test-run-settings-properties.md).

## <a name="see-also"></a>Consulte também

- [Analisar resultados de teste de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analisando violações de regra de limite](../test/analyze-threshold-rule-violations-in-load-tests.md)