---
title: Adicionar marcações de computador a mapas do conjunto de contadores para testes de carga no Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, counter set mappings, computer tags
ms.assetid: f52a73e1-036a-4b28-a6c8-848284bf4488
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 26a0ffc5835e79ee02d1041c4e228f59bcd87d37
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-computer-tags-to-counter-set-mappings-using-the-load-test-editor"></a>Como adicionar marcações de computador a mapeamentos do conjunto de contadores usando o Editor de Teste de Carga

Os marcadores de computador permitem identificar um computador com um nome fácil de reconhecer. As marcações são exibidas no nó **Mapeamentos de conjuntos de contadores** da árvore no Editor de Teste de Carga. O mais importante é que os marcadores são exibidos em relatórios do Excel, o que ajuda os participantes a identificar qual função o computador tem no teste de carga. Por exemplo, "Web Server1 em lab2" ou "SQL Server2 em Phoenix office". Para obter mais informações, consulte [Relatando resultados de teste de carga para comparações de testes ou análise de tendências](../test/compare-load-test-results.md).

## <a name="to-add-a-tag-to-a-computer"></a>Para adicionar uma marca para um computador

1.  Abra um teste de carga.

2.  Escolha o botão **Gerenciar conjuntos de contadores**.

     – ou –

     Clique com o botão direito do mouse na pasta **Conjuntos de contadores** na árvore do teste de carga e escolha **Gerenciar conjuntos de contadores**.

     A caixa de diálogo **Gerenciar conjuntos de contadores** é exibida.

3.  (Opcional) Na caixa de listagem **Computadores e conjuntos de contadores selecionados serão adicionados nas seguintes configurações de execução**, selecione outra configuração de execução.

    > [!NOTE]
    > Isso se aplicará apenas se você tiver mais de uma configuração de execução no teste de carga.

4.  Em **Computador e conjuntos de contadores a monitorar**, selecione o computador ao qual deseja aplicar a marcação.

    > [!NOTE]
    > Para obter informações sobre como adicionar um computador, consulte [Como gerenciar conjuntos de contadores](../test/how-to-manage-counter-sets-using-the-load-test-editor.md).

5.  Na caixa de texto **Marcadores de computador**, digite uma marcação a ser associada ao computador. Por exemplo, "TestMachine12 em lab3".

6.  Escolha **OK**.

## <a name="see-also"></a>Consulte também

- [Analisando violações de regra de limite](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Analisar resultados de teste de carga](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Especificando os conjuntos de contadores e as regras de limite para computadores em um teste de carga](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Como gerenciar conjuntos de contadores](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)