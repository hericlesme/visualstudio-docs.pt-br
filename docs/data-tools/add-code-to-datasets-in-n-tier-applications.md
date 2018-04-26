---
title: Adicione o código a conjuntos de dados em aplicativos de n camadas
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 6de192b07552b4516aa8289e2a68fa90830b7fe8
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Adicione o código a conjuntos de dados em aplicativos de n camadas
Você pode estender a funcionalidade de um conjunto de dados, criando um arquivo de classe parcial para o conjunto de dados e adicionando o código a ele (em vez de adicionar código para o *DatasetName*. Arquivo de DataSet). Classes parciais permitem que o código para uma classe específica ser dividida entre vários arquivos físicos. Para obter mais informações, consulte [parcial](/dotnet/visual-basic/language-reference/modifiers/partial) ou [Classes e métodos Partial](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

O código que define um conjunto de dados é gerado sempre que forem feitas alterações a definição de conjunto de dados (no conjunto de dados tipado). Esse código também é gerado quando você fizer alterações durante a execução de qualquer assistente que modifica a configuração de um conjunto de dados. Para impedir que seu código seja excluído durante a regeneração de um conjunto de dados, adicione código ao arquivo de classe parcial do conjunto de dados.

Por padrão, após você separar o dataset e TableAdapter o código, o resultado é um arquivo de classe distintas em cada projeto. O projeto original tem um arquivo chamado *DatasetName*. VB (ou *DatasetName*. Designer.cs) que contém o código do TableAdapter. O projeto que é designado no **projeto Dataset** propriedade tem um arquivo chamado *DatasetName*. DataSet.Designer.vb (ou *DatasetName*. DataSet.Designer.cs). Este arquivo contém o código do conjunto de dados.

> [!NOTE]
>  Quando você separar conjuntos de dados e TableAdapters (definindo o **projeto DataSet** propriedade), classes parciais dataset existentes no projeto não ser movidas automaticamente. Classes parciais dataset existente devem ser movidas manualmente para o projeto de conjunto de dados.

> [!NOTE]
>  Quando o código de validação deve ser adicionado, o conjunto de dados tipado fornece funcionalidade para gerar <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> manipuladores de eventos. Para obter mais informações, consulte [adicionar validação a um conjunto de dados de n camadas](../data-tools/add-validation-to-an-n-tier-dataset.md).

## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>Para adicionar código a conjuntos de dados em aplicativos de n camadas

1.  Localize o projeto que contém o arquivo. xsd.

2.  Selecione o **. xsd** arquivo para abrir o conjunto de dados.

3.  Clique com botão direito a tabela de dados ao qual você deseja adicionar código (o nome da tabela na barra de título) e, em seguida, selecione **Exibir código**.

     Uma classe parcial é criada e é aberto no Editor de códigos.

4.  Adicione o código dentro da declaração de classe parcial.

     O exemplo a seguir mostra onde adicionar código para o CustomersDataTable in a NorthwindDataSet:

    ```vb
    Partial Public Class CustomersDataTable
        ' Add code here to add functionality
        ' to the CustomersDataTable.
    End Class
    ```
    ```csharp
    partial class CustomersDataTable
    {
        // Add code here to add functionality
        // to the CustomersDataTable.
    }
    ```

## <a name="see-also"></a>Consulte também

- [Visão geral de aplicativos de dados de N camadas](../data-tools/n-tier-data-applications-overview.md)
- [Adicionar código a TableAdapters em aplicativos de N camadas](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Crie e Configure os TableAdapters](create-and-configure-tableadapters.md)
- [Visão geral da atualização hierárquica](hierarchical-update.md)
- [Ferramentas de conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)