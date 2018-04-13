---
title: Selecionar configuração de execução para um teste de carga no Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, run settings, active
ms.assetid: ed6ff546-acfa-4dd8-b3a2-6e7455930ca4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: b1add51256fa43a60640845ae418f7cc9f0a1bbf
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-select-the-active-run-setting-for-a-load-test"></a>Como selecionar a configuração de execução ativa para um teste de carga

Depois de criar seu teste de carga com o **Novo Assistente de Teste de Carga**, você poderá usar o **Editor de Teste de Carga** para alterar as propriedades de cenários para que eles atendam às suas metas e necessidades de teste.

Um teste de carga pode conter uma ou mais *configurações de execução*, que são um conjunto de propriedades que influenciam como um teste de carga é executado. As configurações de execução são organizadas por categorias na janela Propriedades. Quando é executado, um teste de carga usa a configuração de execução definida como ativa no momento.

> [!NOTE]
> Para obter uma lista completa das propriedades das configurações de execução e suas descrições, consulte [Propriedades de configurações de execução de teste de carga](../test/load-test-run-settings-properties.md).

Se o teste de carga contiver apenas um nó de configuração de execução na pasta **Configurações de Execução**, esse nó sempre será o nó ativo. Se o teste de carga contiver vários nós de configurações de execução, você poderá selecionar um para usar ao executar um teste de carga. Consulte [Como adicionar configurações de execução adicionais a um teste de carga](../test/how-to-add-additional-run-settings-to-a-load-test.md).

No Editor de testes de carga, a configuração de execução ativa é identificada pelo sufixo "[Active]".

## <a name="selecting-the-active-run-setting"></a>Selecionando a configuração de execução ativa

### <a name="to-select-the-active-run-setting-in-a-load-test"></a>Para selecionar a configuração de execução ativa em um teste de carga

1.  Abra um teste de carga.

2.  Expanda a pasta **Configurações de Execução**.

3.  Clique com o botão direito do mouse no nó de configurações de execução que você quer que seja o nó ativo e escolha **Definir como ativo**.

     No **Editor de Teste de Carga**, o nó de configuração de execução afetado é atualizado com o sufixo "[Active]".

     A configuração de execução selecionada torna-se ativa, e permanece ativa até que você selecione uma configuração de execução para ser ativa.

> [!NOTE]
>  Você pode substituir a configuração de execução ativa definindo uma variável de ambiente denominada `Test.UseRunSetting=<run setting name>`. Isso é útil quando você executa um teste de carga a partir da linha de comando ou de um arquivo em lotes. Isso permite escolher configurações de execução diferentes sem abrir o teste de carga.

## <a name="specifying-the-run-setting-to-use-from-the-command-line"></a>Especificando a configuração de execução a ser usada na linha de comando
 Você pode substituir as configurações de execução padrão no teste de carga definindo uma variável de ambiente na linha de comando:

 **Set Test.UseRunSetting=PreProdEnvironment**

 E o teste a ser executado:

 **mstest /testcontainer:loadtest1.loadtest**

## <a name="see-also"></a>Consulte também

- [Definindo configurações de execução de teste de carga](../test/configure-load-test-run-settings.md)
- [Especificando os conjuntos de contadores e as regras de limite para computadores em um teste de carga](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Como adicionar configurações de execução adicionais a um teste de carga](../test/how-to-add-additional-run-settings-to-a-load-test.md)