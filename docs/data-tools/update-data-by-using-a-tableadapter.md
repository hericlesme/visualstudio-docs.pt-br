---
title: Atualizar dados usando um TableAdapter
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], saving
- data [Visual Studio], TableAdapters
- updating data, TableAdapters
- TableAdapters, updating data
- data [Visual Studio], updating
- saving data
ms.assetid: 5e32e10e-9bac-4969-9bdd-b8f6919d3516
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 05a61aa42c086ba3fd0a71fa221426c763df14d7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="update-data-by-using-a-tableadapter"></a>Atualizar dados usando um TableAdapter

Depois que os dados no conjunto de dados foi modificados e validados, você pode enviar os dados atualizados para um banco de dados chamando o `Update` método de um [TableAdapter](../data-tools/create-and-configure-tableadapters.md). O `Update` método atualiza uma única tabela de dados e executa o comando correto (INSERT, UPDATE ou DELETE) com base no <xref:System.Data.DataRow.RowState%2A> de cada linha de dados na tabela. Quando um conjunto de dados tiver tabelas relacionadas, o Visual Studio gera uma classe de TableAdapterManager que você usa para fazer as atualizações. A classe de TableAdapterManager garante que as atualizações são feitas na ordem correta com base nas restrições de chave estrangeira são definidas no banco de dados. Quando você usa os controles de associação de dados, a arquitetura de associação de dados cria uma variável de membro da classe TableAdapterManager chamada tableAdapterManager.

> [!NOTE]
> Quando você tenta atualizar uma fonte de dados com o conteúdo de um conjunto de dados, você poderá obter erros. Para evitar erros, recomendamos que você coloque o código que chama o adaptador `Update` método dentro de um `try` / `catch` bloco.

 O procedimento exato para atualizar uma fonte de dados pode variar dependendo das necessidades de negócios, mas inclui as seguintes etapas:

1.  Chamar o adaptador `Update` método em um `try` / `catch` bloco.

2.  Se uma exceção for detectada, localize a linha de dados que causou o erro.

3.  Reconcilie o problema nos dados de linha (programaticamente se possível, ou apresentando a linha inválida para o usuário para modificação) e, em seguida, tente novamente a atualização (<xref:System.Data.DataRow.HasErrors%2A>, <xref:System.Data.DataTable.GetErrors%2A>).

## <a name="save-data-to-a-database"></a>Salvar dados em um banco de dados

Chamar o `Update` método de um TableAdapter. Passe o nome da tabela de dados que contém os valores a serem gravados no banco de dados.

### <a name="to-update-a-database-by-using-a-tableadapter"></a>Para atualizar um banco de dados usando um TableAdapter

-   Coloque o TableAdapter`Update` método em um `try` / `catch` bloco. O exemplo a seguir mostra como atualizar o conteúdo do `Customers` tabela `NorthwindDataSet` de dentro um `try` / `catch` bloco.

     [!code-csharp[VbRaddataSaving#9](../data-tools/codesnippet/CSharp/update-data-by-using-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataSaving#9](../data-tools/codesnippet/VisualBasic/update-data-by-using-a-tableadapter_1.vb)]

## <a name="see-also"></a>Consulte também

- [Salvar dados de volta no banco de dados](../data-tools/save-data-back-to-the-database.md)