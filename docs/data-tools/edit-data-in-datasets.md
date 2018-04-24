---
title: Editar dados em conjuntos de dados
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f9acc81270ecf9c0dfc60d3e1cfed524e0ce97f5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="edit-data-in-datasets"></a>Editar dados em conjuntos de dados
Você editar dados em tabelas de dados, assim como você editar os dados em uma tabela em qualquer banco de dados. O processo pode incluir inserir, atualizar e excluir registros na tabela. Em um formulário de associação de dados, você pode especificar quais campos são editáveis pelo usuário. Nesses casos, a infraestrutura de associação de dados trata todos os controle de alterações para que as alterações podem ser enviadas no banco de dados mais tarde. Se você programaticamente fazer edições em dados e quiser enviar essas alterações no banco de dados, você deve usar os objetos e métodos que fazem o controle de alterações para você.

Além de alterar os dados reais, você também pode consultar um <xref:System.Data.DataTable> para retornar linhas específicas de dados. Por exemplo, você pode consultar as linhas individuais, versões específicas de linhas (originais e propostas), linhas que foram alteradas ou linhas com erros.

## <a name="to-edit-rows-in-a-dataset"></a>Para editar linhas em um conjunto de dados
Para editar uma linha existente em um <xref:System.Data.DataTable>, você precisa localizar o <xref:System.Data.DataRow> você deseja editar e, em seguida, atribuir os valores atualizados para as colunas desejadas.

Se você não souber o índice da linha você deseja editar, use o `FindBy` método para pesquisar a chave primária:

[!code-csharp[VbRaddataEditing#3](../data-tools/codesnippet/CSharp/edit-data-in-datasets_1.cs)]
[!code-vb[VbRaddataEditing#3](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_1.vb)]

Se você souber o índice de linha, você pode acessar e edita linhas da seguinte maneira:

[!code-csharp[VbRaddataEditing#5](../data-tools/codesnippet/CSharp/edit-data-in-datasets_2.cs)]
[!code-vb[VbRaddataEditing#5](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_2.vb)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Para inserir novas linhas em um conjunto de dados
Aplicativos que usam controles associados a dados normalmente adicionam novos registros através de **adicionar novo** botão um [controle BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms).

Para adicionar novos registros manualmente para um conjunto de dados, crie uma nova linha de dados chamando o método no DataTable. Em seguida, adicione a linha para o <xref:System.Data.DataRow> coleção (<xref:System.Data.DataTable.Rows%2A>) da <xref:System.Data.DataTable>:

[!code-csharp[VbRaddataEditing#1](../data-tools/codesnippet/CSharp/edit-data-in-datasets_3.cs)]
[!code-vb[VbRaddataEditing#1](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_3.vb)]

Para manter as informações que o dataset precisa para enviar atualizações para a fonte de dados, use o <xref:System.Data.DataRow.Delete%2A> método para remover as linhas em uma tabela de dados. Por exemplo, se seu aplicativo usa um TableAdapter (ou <xref:System.Data.Common.DataAdapter>), o TableAdapter `Update` método exclui as linhas no banco de dados que têm um <xref:System.Data.DataRow.RowState%2A> de <xref:System.Data.DataRowState.Deleted>.

Se seu aplicativo não precisa enviar atualizações de volta para uma fonte de dados, em seguida, é possível remover registros acessando diretamente a coleta de linha de dados (<xref:System.Data.DataRowCollection.Remove%2A>).

#### <a name="to-delete-records-from-a-data-table"></a>Para excluir registros de uma tabela de dados

-   Chamar o <xref:System.Data.DataRow.Delete%2A> método de um <xref:System.Data.DataRow>.

     Esse método não remove o registro fisicamente. Em vez disso, ele marca o registro para exclusão.

    > [!NOTE]
    >  Se você receber a propriedade count de um <xref:System.Data.DataRowCollection>, a contagem resultante inclui registros que foram marcados para exclusão. Para obter uma contagem precisa de registros que não estão marcados para exclusão, você pode fazer um loop através da coleção examinando o <xref:System.Data.DataRow.RowState%2A> propriedade de cada registro. (Registros marcados para exclusão têm um <xref:System.Data.DataRow.RowState%2A> de <xref:System.Data.DataRowState.Deleted>.) Como alternativa, você pode criar uma exibição de dados de um conjunto de dados que filtra com base no estado de linha e obter a propriedade count de lá.

O exemplo a seguir mostra como chamar o <xref:System.Data.DataRow.Delete%2A> método para marcar a primeira linha a `Customers` como excluído de tabela:

[!code-csharp[VbRaddataEditing#8](../data-tools/codesnippet/CSharp/edit-data-in-datasets_4.cs)]
[!code-vb[VbRaddataEditing#8](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_4.vb)]

## <a name="determine-if-there-are-changed-rows"></a>Determinar se há linhas alteradas
Quando alterações são feitas em registros em um conjunto de dados, informações sobre essas alterações são armazenadas até que você confirme-los. Confirmar as alterações ao chamar o `AcceptChanges` método de uma conjunto de dados ou tabela de dados, ou quando você chamar o `Update` método de um TableAdapter ou adaptador de dados.

As alterações são controladas de duas maneiras em cada linha de dados:

-   Cada linha de dados contém informações relacionadas à sua <xref:System.Data.DataRow.RowState%2A> (por exemplo, <xref:System.Data.DataRowState.Added>, <xref:System.Data.DataRowState.Modified>, <xref:System.Data.DataRowState.Deleted>, ou <xref:System.Data.DataRowState.Unchanged>).

-   Cada linha de dados alterada contém várias versões de linha (<xref:System.Data.DataRowVersion>), a versão original (antes de alterações) e a versão atual (após alterações). Durante o período quando uma alteração é pendente (o tempo em que você pode responder ao <xref:System.Data.DataTable.RowChanging> evento), uma terceira versão — a versão proposta — também está disponível.

O <xref:System.Data.DataSet.HasChanges%2A> método de um conjunto de dados retorna `true` se foram feitas alterações no conjunto de dados. Depois de determinar a existam de linhas alteradas, você pode chamar o `GetChanges` método de um <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> para retornar um conjunto de linhas alteradas.

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Para determinar se foram feitas alterações para todas as linhas

-   Chamar o <xref:System.Data.DataSet.HasChanges%2A> método de um conjunto de dados para verificar se há alterado linhas.

O exemplo a seguir mostra como verificar o valor de retorno de <xref:System.Data.DataSet.HasChanges%2A> método para detectar se há quaisquer linhas alteradas em um dataset chamado `NorthwindDataset1`:

[!code-csharp[VbRaddataEditing#12](../data-tools/codesnippet/CSharp/edit-data-in-datasets_5.cs)]
[!code-vb[VbRaddataEditing#12](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_5.vb)]

## <a name="determine-the-type-of-changes"></a>Determinar o tipo de alterações
Você também pode verificar ver que tipo de alterações foram feitas em um conjunto de dados, passando um valor da <xref:System.Data.DataRowState> enumeração para o <xref:System.Data.DataSet.HasChanges%2A> método.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Para determinar quais tipos de alterações foram feitas em uma linha

-   Passar um <xref:System.Data.DataRowState> o valor para o <xref:System.Data.DataSet.HasChanges%2A> método.

O exemplo a seguir mostra como verificar um dataset chamado `NorthwindDataset1` para determinar se as novas linhas foram adicionadas a ela:

[!code-csharp[VbRaddataEditing#13](../data-tools/codesnippet/CSharp/edit-data-in-datasets_6.cs)]
[!code-vb[VbRaddataEditing#13](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_6.vb)]

## <a name="to-locate-rows-that-have-errors"></a>Para localizar linhas com erros
Ao trabalhar com colunas individuais e linhas de dados, você poderá encontrar erros. Você pode verificar o `HasErrors` propriedade para determinar se existem erros em um <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, ou <xref:System.Data.DataRow>.

1.  Verifique o `HasErrors` propriedade para ver se há erros no conjunto de dados.

2.  Se o `HasErrors` é de propriedade `true`, iterar por meio de coleções de tabelas e, em seguida, pelas linhas, para encontrar a linha com o erro.

[!code-csharp[VbRaddataEditing#23](../data-tools/codesnippet/CSharp/edit-data-in-datasets_7.cs)]
[!code-vb[VbRaddataEditing#23](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_7.vb)]

## <a name="see-also"></a>Consulte também

- [Ferramentas de conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)