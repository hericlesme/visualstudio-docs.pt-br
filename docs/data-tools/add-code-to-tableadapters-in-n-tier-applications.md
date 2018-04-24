---
title: Adicionar código a TableAdapters em aplicativos de n camadas
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 165d0e76eb030d8a173761733245c993115ed315
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Adicionar código a TableAdapters em aplicativos de n camadas
Você pode estender a funcionalidade de um TableAdapter, criando um arquivo de classe parcial para o TableAdapter e adicionando o código a ele (em vez de adicionar código para o *DatasetName*. Arquivo de DataSet). Classes parciais permitem que o código para uma classe específica ser dividida entre vários arquivos físicos. Para obter mais informações, consulte [parcial](/dotnet/visual-basic/language-reference/modifiers/partial) ou [partial (tipo)](/dotnet/csharp/language-reference/keywords/partial-type).

O código que define um TableAdapter é gerado sempre que forem feitas alterações no TableAdapter no conjunto de dados. Esse código também é gerado quando as alterações são feitas durante a execução de qualquer assistente que modifica a configuração do TableAdapter. Para impedir que seu código seja excluído durante a regeneração de um TableAdapter, adicione código ao arquivo de classe parcial do TableAdapter.

Por padrão, após você separar o dataset e TableAdapter o código, o resultado é um arquivo de classe distintas em cada projeto. O projeto original tem um arquivo chamado *DatasetName*. VB (ou *DatasetName*. Designer.cs) que contém o código do TableAdapter. O projeto que é designado no **projeto Dataset** propriedade tem um arquivo chamado *DatasetName*. DataSet.Designer.vb (ou *DatasetName*. DataSet.Designer.cs) que contém o código do conjunto de dados.

> [!NOTE]
>  Quando você separar conjuntos de dados e TableAdapters (definindo o **projeto DataSet** propriedade), classes parciais dataset existentes no projeto não serão movidas automaticamente. Classes parciais dataset existentes devem ser movidas manualmente para o projeto de conjunto de dados.

> [!NOTE]
> O conjunto de dados fornece funcionalidade para gerar <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> manipuladores de eventos quando a validação é necessária. Para obter mais informações, consulte [adicionar validação a um conjunto de dados de n camadas](../data-tools/add-validation-to-an-n-tier-dataset.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Para adicionar código de usuário a um TableAdapter em um aplicativo de n camadas

1.  Localize o projeto que contém o arquivo. xsd.

2.  Clique duas vezes o **. xsd** arquivo para abrir o **Dataset Designer**.

3.  Clique com botão direito no TableAdapter que você deseja adicionar código para e, em seguida, selecione **Exibir código**.

     Uma classe parcial é criada e é aberto no Editor de códigos.

4.  Adicione o código dentro da declaração de classe parcial.

5.  O exemplo a seguir mostra onde adicionar código para o `CustomersTableAdapter` no `NorthwindDataSet`:

    ```vb
    Partial Public Class CustomersTableAdapter
        ' Add code here to add functionality
        ' to the CustomersTableAdapter.
    End Class
    ```

    ```csharp
    public partial class CustomersTableAdapter
    {
        // Add code here to add functionality
        // to the CustomersTableAdapter.
    }
    ```

## <a name="see-also"></a>Consulte também

- [Visão geral de aplicativos de dados de N camadas](../data-tools/n-tier-data-applications-overview.md)
- [Como adicionar código a conjuntos de dados em aplicativos de N camadas](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Crie e Configure os TableAdapters](create-and-configure-tableadapters.md)
- [Visão geral da atualização hierárquica](hierarchical-update.md)
