---
title: Como especificar a taxa de amostra para uma configuração de execução de teste de carga no Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings
ms.assetid: 51cbe7d6-5dfd-4842-bca3-f7f8a665dc84
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 18fa71396caa0c164ef7f37183cda28c701cf4f8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-specify-the-sample-rate-for-a-load-test-run-setting"></a>Como especificar a taxa de amostra para uma configuração de execução de teste de carga

Depois de criar seu teste de carga com o **Novo Assistente de Teste de Carga**, você poderá usar o **Editor de Teste de Carga** para alterar as propriedades de forma que elas atendam às suas metas e necessidades de teste.

Usando o **Editor de Teste de Carga**, você pode editar um valor da propriedade **Taxa de Amostragem** das configurações de execução na janela **Propriedades**. Para obter uma lista completa das propriedades das configurações de execução e suas descrições, consulte [Propriedades de configurações de execução de teste de carga](../test/load-test-run-settings-properties.md).

Escolha um valor para a propriedade **Taxa de Amostragem** da configuração de execução de teste de carga com base na duração do seu teste de carga. Uma taxa de amostragem menor, como o valor padrão de cinco segundos, requer mais espaço no banco de dados dos resultados de testes de carga. Para testes de carga mais longos, aumentar a taxa de amostragem reduzirá a quantidade de dados coletados. Para obter mais informações, consulte [Como especificar a taxa de amostragem para uma configuração de execução de teste de carga](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Veja algumas diretrizes para taxas de amostragem:

|Duração do teste de carga|Taxa de amostragem recomendada|
|------------------------|-----------------------------|
|\< 1 hora|5 segundos|
|1 a 8 horas|15 segundos|
|8 a 24 horas|30 segundos|
|> 24 horas|60 segundos|

## <a name="to-specify-performance-counter-sampling-rate-in-a-run-setting"></a>Para especificar a taxa de amostragem do contador de desempenho em uma configuração de execução

1.  Abra um teste de carga.

     O **Editor de Teste de Carga** é exibido. A árvore do teste de carga é exibida.

2.  Na árvore de teste de carga, na pasta **Configurações de Execução**, escolha a configuração de execução para a qual deseja especificar a taxa de amostragem.

3.  No menu **Exibir**, selecione **Janela de Propriedades**.

     As categorias e as propriedades da configuração de execução de carga são exibidas na janela Propriedades.

4.  Na propriedade **Taxa de Amostragem**, insira um valor temporal que indique a frequência com que o teste de carga coletará dados de contador de desempenho.

5.  Depois de alterar a propriedade, escolha **Salvar** no menu **Arquivo**. Em seguida, você pode executar o teste de carga usando o novo valor de **Taxa de Amostragem**.

## <a name="see-also"></a>Consulte também

- [Definindo configurações de execução de teste de carga](../test/configure-load-test-run-settings.md)
- [Propriedades do cenário de teste de carga](../test/load-test-scenario-properties.md)