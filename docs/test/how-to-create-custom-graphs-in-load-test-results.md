---
title: Como criar gráficos personalizados em resultados de teste de carga no Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load test results graphs, creating
- load test results graphs
ms.assetid: 17fcafce-76f9-4411-9389-6e5376eab236
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 38249ef2a655f2dc30ad5536f1d47f94cff54181
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-custom-graphs-in-load-test-results"></a>Como criar gráficos personalizados em resultados de teste de carga

Você pode projetar gráficos que exibam informações específicas sobre resultados de teste de carga. Você cria um gráfico personalizado especificando os contadores de teste de carga que o gráfico exibirá.

 Você pode executar o procedimento a seguir enquanto um teste de carga está em execução ou depois de concluir a execução.

## <a name="to-create-a-custom-load-test-results-graph"></a>Para criar um grafo de resultados de teste de carga personalizado

1.  Na barra de ferramentas Teste de Carga, escolha **Adicionar um novo gráfico**.

     \- ou -

     No Analisador de Teste de Carga, clique com o botão direito do mouse no painel Contadores ou em um gráfico e, em seguida, selecione **Adicionar Gráfico**.

     A caixa de diálogo **Digite o nome do gráfico** é exibida.

2.  Em **Nome do gráfico**, digite um nome para o gráfico e escolha **OK**.

     O novo gráfico aparece no Analisador de Testes de Carga. Ele é exibido no painel de gráfico selecionado no momento; ele substitui o gráfico que foi exibido nesse painel.

3.  Personalize o novo gráfico adicionando contadores. Para obter mais informações, consulte [Como adicionar e excluir contadores em gráficos](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md).

## <a name="see-also"></a>Consulte também

- [Analisar resultados de teste de carga na exibição de gráficos](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Como adicionar e excluir contadores em gráficos](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)