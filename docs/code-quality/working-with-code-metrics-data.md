---
title: "Resultados de métricas no Visual Studio de código | Microsoft Docs"
ms.custom: 
ms.date: 12/12/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c259a1d303c741d4e36af46250073b0378a65f8b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-code-metrics-data"></a>Trabalhando com dados de métricas de código

O **resultados de métricas de código** janela exibe os dados que são gerados pela análise de métricas de código. Para obter mais informações sobre valores de dados de métricas de código, consulte [valores de métricas de código](../code-quality/code-metrics-values.md).

## <a name="displaying-code-metrics-results"></a>Exibindo resultados de métricas de código

O **resultados de métricas de código** janela é exibida automaticamente quando você gerar resultados de métricas de código. Você também pode exibir a janela a qualquer momento.

### <a name="to-display-the-code-metrics-results-window"></a>Para exibir a janela de resultados de métricas de código

- Sobre o **analisar** menu, escolha **Windows** > **resultados de métricas de código**.

   \- ou -

- Sobre o **exibição** menu, escolha **outras janelas** > **resultados de métricas de código**.

   O **resultados de métricas de código** janela é exibida, mesmo se ele não contém nenhum resultado.

### <a name="to-view-code-metrics-details"></a>Para exibir detalhes de métricas de código

Se os resultados de métricas de código foram gerados, expanda a árvore no **hierarquia** coluna.

## <a name="filtering-code-metrics-results"></a>Filtrando resultados de métricas de código

Você pode filtrar os resultados que são exibidos na **resultados de métricas de código** janela usando a barra de ferramentas na parte superior. Por exemplo, você talvez queira ver apenas os resultados que tem um índice de facilidade de manutenção abaixo 65.

O **filtro** caixa suspensa contém os nomes das colunas de resultados. Quando um filtro é definido, ele é adicionado à parte inferior da lista, junto com um recuo. A lista pode conter os dez últimos filtros que foram definidos.

### <a name="to-filter-the-code-metrics-results"></a>Para filtrar os resultados de métricas de código

1.  Do **filtro** , selecione o nome da coluna.

2.  Em **Min**, digite o valor mínimo a ser exibido.

3.  Em **Max**, digite o valor máximo a ser exibido.

4.  Clique o **Aplicar filtro** botão.

5.  Para ver os detalhes do resultado, expanda a árvore de hierarquia.

## <a name="adding-removing-and-rearranging-data-columns"></a>Adicionar, remover e reorganizar as colunas de dados

Você pode adicionar ou remover colunas para os resultados de **resultados de métricas de código** janela. Além disso, você pode reorganizar as colunas de resultados para que apareçam na ordem em que você deseja.

### <a name="to-remove-a-column"></a>Para remover uma coluna

1. Clique o **Adicionar/remover colunas** botão.

     \-ou - clique qualquer cabeçalho de coluna e, em seguida, clique em **Adicionar/remover colunas**.

1. No **Adicionar/remover colunas** caixa de diálogo, desmarque a caixa de seleção para a coluna que você deseja remover e, em seguida, clique em **Okey**.

### <a name="to-add-a-previously-removed-column"></a>Para adicionar uma coluna removida anteriormente

1. Clique o **Adicionar/remover colunas** botão.

     \- ou -

     Clique em qualquer cabeçalho de coluna e, em seguida, clique em **Adicionar/remover colunas**.

1. No **Adicionar/remover colunas** caixa de diálogo caixa, marque a caixa de seleção para a coluna que você deseja adicionar e, em seguida, clique em **Okey**.

### <a name="to-rearrange-columns"></a>Para reorganizar colunas

1. Clique o **Adicionar/remover colunas** botão.

     \- ou -

     Clique em qualquer cabeçalho de coluna e, em seguida, clique em **Adicionar/remover colunas**.

1. No **Adicionar/remover colunas** caixa de diálogo, selecione a coluna que você deseja mover e, em seguida, clique na seta para cima ou seta para baixo.

1. Quando a coluna é posicionada onde desejar, clique em **Okey**.

## <a name="copying-data-to-the-clipboard-or-excel"></a>Copiando dados para a área de transferência ou o Excel

Você pode selecionar e copiar uma linha de dados de métricas de código selecionada para a área de transferência como uma cadeia de caracteres de texto que contém uma linha para o nome e valor de cada coluna de dados. Você também pode clicar em **abrir seleção no Microsoft Excel** para exportar todos os resultados de métricas de código para uma planilha do Excel.

## <a name="creating-a-work-item-based-on-code-metric-results"></a>Criando um item de trabalho com base nos resultados de métricas de código

Você pode criar um [Visual Studio Team Services (VSTS)](/vsts/index) resulta de item de trabalho que se baseia no **resultados de métrica de código** janela. Quando o item de trabalho é criado, o Visual Studio automaticamente entra em um título de **título** dados de métricas de campo e o código sob o **histórico** guia.

Para obter mais informações sobre VSTS itens de trabalho, consulte [(VSTS) de itens de trabalho](/vsts/work/work-items/index).

### <a name="to-create-a-work-item-based-on-a-result"></a>Para criar um item de trabalho com base em um resultado

1.  Clique o resultado.

2.  Aponte para **Criar Item de trabalho**e, em seguida, clique no tipo de item de trabalho que você deseja criar (**Bug**, **tarefa**, e assim por diante).

3.  Conclua o formulário de item de trabalho com o preenchimento de todos os campos obrigatórios.

4.  Sobre o **arquivo** menu, clique em **Salvar tudo** para salvar o item de trabalho.

### <a name="to-create-a-bug-based-on-a-result"></a>Para criar um bug com base em um resultado

1.  Clique no resultado para selecioná-lo.

2.  Clique o **Criar Item de trabalho** botão.

3.  Conclua o formulário de item de trabalho com o preenchimento de todos os campos obrigatórios.

4.  Sobre o **arquivo** menu, clique em **Salvar tudo** para salvar o item de trabalho.

## <a name="see-also"></a>Consulte também

[Valores de métricas de código](../code-quality/code-metrics-values.md)  
[Como gerar dados de métricas do código](../code-quality/how-to-generate-code-metrics-data.md)