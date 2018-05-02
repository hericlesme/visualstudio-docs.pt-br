---
title: Definir as configurações de execução de teste de carga do Visual Studio usando a linha de comando
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, command line
- load tests, run settings, selecting
ms.assetid: 175d1d58-f09a-4449-b132-a29a394a7c8e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 40186bde515c95638ae0bdd90b9cace92b8da4a5
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-select-a-load-test-run-setting-to-use-from-the-command-line"></a>Como selecionar uma configuração de execução do teste de carga a ser usada na linha de comando

Um teste de carga pode conter uma ou mais *configurações de execução*, que são um conjunto de propriedades que influenciam como um teste de carga é executado. As configurações de execução são organizadas por categorias na janela Propriedades.  Quando é executado, um teste de carga usa a configuração de execução definida como ativa no momento.

 Se contiver apenas uma configuração de execução, o teste de carga será sempre o nó ativo. Se o teste de carga contiver vários nós de configurações de execução, você poderá selecionar um para usar ao executar um teste de carga na linha de comando. Consulte [Como adicionar configurações de execução adicionais a um teste de carga](../test/how-to-add-additional-run-settings-to-a-load-test.md).

## <a name="to-change-the-run-setting-from-the-command-line"></a>Para alterar a configuração de execução na linha de comando

1.  Se quiser usar configurações de execução diferentes na linha de comando para se beneficiar da estratégia do parâmetro de contexto, use o seguinte comando:

    `Set Test.UseRunSetting= CorporateStagingWebServer`

2.  Execute o teste de carga usando mstest:

    `mstest /testcontainer:loadtest1.loadtest`

## <a name="see-also"></a>Consulte também

- [Definindo configurações de execução de teste de carga](../test/configure-load-test-run-settings.md)
- [Especificando os conjuntos de contadores e as regras de limite para computadores em um teste de carga](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Como adicionar configurações de execução adicionais a um teste de carga](../test/how-to-add-additional-run-settings-to-a-load-test.md)
- [Como selecionar a configuração de execução ativa para um teste de carga](../test/how-to-select-the-active-run-setting-for-a-load-test.md)