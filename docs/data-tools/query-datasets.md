---
title: Conjuntos de dados de consulta | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 7b1a91cf-8b5a-4fc0-ac36-0dc2d336fa1b
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 10e37db09efab78b3048ddeab4096325ba00802f
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2017
---
# <a name="query-datasets"></a>Conjuntos de dados de consulta
Para procurar por registros específicos em um conjunto de dados, use o método FindBy no DataTable, escrever sua própria instrução foreach para executar um loop pela coleção de linhas da tabela, ou usar [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).  
  
## <a name="dataset-case-sensitivity"></a>Conjunto de dados diferenciar maiusculas de minúsculas  
Dentro de um conjunto de dados, nomes de tabela e coluna diferenciam maiusculas de minúsculas por padrão — ou seja, uma tabela em um conjunto de dados chamado "Clientes" pode também ser referida como "clientes". Isso coincide com as convenções de nomenclatura em muitos bancos de dados, incluindo o SQL Server. No SQL Server, o comportamento padrão é que os nomes dos elementos de dados não podem ser diferenciados apenas por caso.  
  
> [!NOTE]
>  Ao contrário de conjuntos de dados, documentos XML diferenciam maiusculas de minúsculas, para que os nomes de elementos de dados definidos em esquemas diferenciam maiusculas de minúsculas. Por exemplo, o protocolo de esquema permite que o esquema definir uma tabela chamada "Clientes" e uma tabela diferente chamada "clientes". Isso pode resultar em conflitos de nome quando um esquema que contém elementos que diferenciam somente maiusculas e minúsculas é usado para gerar uma classe de conjunto de dados.  
  
Diferenciação de maiusculas e, no entanto, pode ser um fator em como os dados são interpretados no conjunto de dados. Por exemplo, se você filtrar os dados em uma tabela de conjunto de dados, os critérios de pesquisa podem retornar resultados diferentes dependendo se a comparação diferencia maiusculas de minúsculas. Você pode controlar a diferenciação de maiusculas e minúsculas de filtragem, pesquisa e classificação definindo o conjunto de dados <xref:System.Data.DataSet.CaseSensitive%2A> propriedade. Todas as tabelas no conjunto de dados herdam o valor dessa propriedade por padrão. (Você pode substituir essa propriedade para cada tabela individual, definindo a tabela <xref:System.Data.DataTable.CaseSensitive%2A> propriedade.)  
  
## <a name="locate-a-specific-row-in-a-data-table"></a>Localizar uma linha específica em uma tabela de dados  
  
#### <a name="to-find-a-row-in-a-typed-dataset-with-a-primary-key-value"></a>Para localizar uma linha em um conjunto de dados tipado com um valor de chave primária  
  
-   Para localizar uma linha, chamar fortemente tipada `FindBy` método que usa a chave primária da tabela.  
  
     No exemplo a seguir, o `CustomerID` coluna é a chave primária do `Customers` tabela. Isso significa que o gerado `FindBy` método é `FindByCustomerID`. O exemplo mostra como atribuir um determinado <xref:System.Data.DataRow> a uma variável usando gerado `FindBy` método.  
  
     [!code-csharp[VbRaddataEditing#18](../data-tools/codesnippet/CSharp/query-datasets_1.cs)]
     [!code-vb[VbRaddataEditing#18](../data-tools/codesnippet/VisualBasic/query-datasets_1.vb)]  
  
#### <a name="to-find-a-row-in-an-untyped-dataset-with-a-primary-key-value"></a>Para localizar uma linha em um conjunto de dados sem tipo com um valor de chave primária  
  
-   Chamar o <xref:System.Data.DataRowCollection.Find%2A> método de um <xref:System.Data.DataRowCollection> coleção, passando a chave primária como um parâmetro.  
  
     O exemplo a seguir mostra como declarar uma nova linha chamada `foundRow` e atribua-o valor de retorno de <xref:System.Data.DataRowCollection.Find%2A> método. Se a chave primária for encontrada, o conteúdo do índice da coluna 1 é exibido em uma caixa de mensagem.  
  
     [!code-csharp[VbRaddataEditing#19](../data-tools/codesnippet/CSharp/query-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#19](../data-tools/codesnippet/VisualBasic/query-datasets_2.vb)]  
  
## <a name="find-rows-by-column-values"></a>Localizar linhas por valores de coluna  
  
#### <a name="to-find-rows-based-on-the-values-in-any-column"></a>Para localizar linhas com base nos valores em qualquer coluna  
  
-   Tabelas de dados são criadas com o <xref:System.Data.DataTable.Select%2A> método, que retorna uma matriz de <xref:System.Data.DataRow>s baseada na expressão passada para o <xref:System.Data.DataTable.Select%2A> método. Para obter mais informações sobre como criar expressões válidas, consulte a seção "Sintaxe de expressão" da página o <xref:System.Data.DataColumn.Expression%2A> propriedade.  
  
     O exemplo a seguir mostra como usar o <xref:System.Data.DataTable.Select%2A> método o <xref:System.Data.DataTable> para localizar linhas específicas.  
  
     [!code-csharp[VbRaddataEditing#20](../data-tools/codesnippet/CSharp/query-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#20](../data-tools/codesnippet/VisualBasic/query-datasets_3.vb)]  
  
## <a name="access-related-records"></a>Registros relacionados de acesso  
Quando as tabelas em um dataset estão relacionadas, um <xref:System.Data.DataRelation> objeto pode disponibilizar os registros relacionados em outra tabela. Por exemplo, um conjunto de dados que contém `Customers` e `Orders` tabelas podem ser disponibilizadas.  
  
Você pode usar um <xref:System.Data.DataRelation> objeto para localizar registros relacionados chamando o <xref:System.Data.DataRow.GetChildRows%2A> método de um <xref:System.Data.DataRow> na tabela pai. Esse método retorna uma matriz de registros filho relacionados. Ou você pode chamar o <xref:System.Data.DataRow.GetParentRow%2A> método de um <xref:System.Data.DataRow> na tabela filho. Esse método retorna um único <xref:System.Data.DataRow> da tabela pai.  
  
Esta página fornece exemplos que usam conjuntos de dados tipados. Para obter informações sobre como navegar em relações em datasets não tipados, consulte [DataRelations navegando](/dotnet/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations).  
  
> [!NOTE]
>  Se você estiver trabalhando em um aplicativo Windows Forms e usando os recursos de associação de dados para exibir dados, o formulário gerado pelo designer pode fornecer funcionalidade suficiente para seu aplicativo. Para obter mais informações, consulte [associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Especificamente, consulte [relacionamentos em conjuntos de dados](relationships-in-datasets.md).  
  
Os exemplos de código a seguir demonstram como navegar para cima e relacionamentos em conjuntos de dados tipados. O uso de exemplos de código digitado <xref:System.Data.DataRow>s (`NorthwindDataSet.OrdersRow`) e o FindBy gerado*PrimaryKey* (`FindByCustomerID`) métodos para localizar uma linha desejada e retornar os registros relacionados. Os exemplos compilam e executam corretamente somente se você tiver:  
  
-   Uma instância de um conjunto de dados chamado `NorthwindDataSet` com um `Customers` tabela.  
  
-   Um `Orders` tabela.  
  
-   Uma relação nomeada `FK_Orders_Customers`relacionando as duas tabelas.  
  
Além disso, ambas as tabelas precisam ser preenchida com dados para todos os registros a serem retornados.  
  
#### <a name="to-return-the-child-records-of-a-selected-parent-record"></a>Para retornar os registros de um registro pai selecionado filho  
  
-   Chamar o <xref:System.Data.DataRow.GetChildRows%2A> método de um determinado `Customers` dados de linha e retornar uma matriz de linhas do `Orders` tabela:  
  
     [!code-csharp[VbRaddataDatasets#6](../data-tools/codesnippet/CSharp/query-datasets_4.cs)]
     [!code-vb[VbRaddataDatasets#6](../data-tools/codesnippet/VisualBasic/query-datasets_4.vb)]  
  
#### <a name="to-return-the-parent-record-of-a-selected-child-record"></a>Para retornar o registro pai de um registro filho selecionado  
  
-   Chamar o <xref:System.Data.DataRow.GetParentRow%2A> método de um determinado `Orders` linha de dados e retornar uma única linha do `Customers` tabela:  
  
     [!code-csharp[VbRaddataDatasets#7](../data-tools/codesnippet/CSharp/query-datasets_5.cs)]
     [!code-vb[VbRaddataDatasets#7](../data-tools/codesnippet/VisualBasic/query-datasets_5.vb)]

## <a name="see-also"></a>Consulte também
[Ferramentas de conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  