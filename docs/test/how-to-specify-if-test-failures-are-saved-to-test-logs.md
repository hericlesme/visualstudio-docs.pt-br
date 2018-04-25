---
title: Salvar log de teste de carga para falhas de teste no Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, logging
ms.assetid: 08a7fe98-a7f7-4b8d-94a3-ec82b65a2aaf
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 17b8792a98473658ae6ac47cd418028ce2cfcf6f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-specify-if-test-failures-are-saved-to-test-logs-using-the-load-test-editor"></a>Como especificar se falhas no teste são salvas em logs de teste usando o Editor de Teste de Carga

Depois de criar seu teste de carga com o **Novo Assistente de Teste de Carga**, você poderá usar o **Editor de Teste de Carga** para alterar as propriedades do teste de carga para que elas atendam às suas metas e necessidades de teste. Consulte [Passo a passo: criar e executar um teste de carga](../test/walkthrough-create-and-run-a-load-test.md). Você pode especificar se deseja que o log de teste seja salvo se um teste falhar em um teste de carga alterando a propriedade **Salvar log em caso de falha do teste**.

> [!NOTE]
>  Para obter uma lista completa das propriedades das configurações de execução e suas descrições, consulte [Propriedades de configurações de execução de teste de carga](../test/load-test-run-settings-properties.md).

## <a name="to-specify-if-the-test-log-is-saved-when-a-test-fails-in-a-scenario"></a>Para especificar se o log de teste será salvo quando um teste falhar em um cenário

1.  Abra um teste de carga.

     O Editor de Testes de Carga é exibido. A árvore do teste de carga é exibida.

2.  Na pasta **Configurações de Execução** das árvores de teste de carga, escolha o nó das configurações de execução para o qual deseja especificar o número máximo de iterações de teste.

3.  No menu **Exibir**, selecione **Janela de Propriedades**.

     As categorias e as propriedades das configurações de execução de carga são exibidas na janela Propriedades.

4.  Na propriedade **Salvar log em caso de falha do teste**, selecione Verdadeiro ou Falso para especificar se você deseja salvar o log de teste em caso de falha do teste no cenário.

     Depois de alterar a propriedade, escolha **Salvar** no menu **Arquivo**.

     Os dados salvos no log podem ser exibidos usando-se a exibição Tabelas do Analisador de Testes de Carga. Para obter mais informações, consulte [Analyze Load Test Results and Errors in the Tables View](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) (Analisar resultados e erros de teste de carga na exibição de tabelas).

## <a name="see-also"></a>Consulte também

- [Editando cenários de teste de carga](../test/edit-load-test-scenarios.md)
- [Passo a passo: criar e executar um teste de carga](../test/walkthrough-create-and-run-a-load-test.md)
- [Editando cenários de teste de carga](../test/edit-load-test-scenarios.md)
- [Como configurar a coleta de detalhes completos para habilitar o gráfico de atividade de usuário virtual](../test/how-to-configure-load-tests-to-collect-full-details.md)
- [Como especificar com que frequência os logs de teste são salvos](../test/how-to-specify-how-frequently-test-logs-are-saved.md)