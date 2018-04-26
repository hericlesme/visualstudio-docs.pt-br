---
title: Adicionar validação a um conjunto de dados de n camadas
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8fbbf6a28d63e755929cc9d8a6c62ff7649b2f1c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Adicionar validação a um conjunto de dados de n camadas
Adicionando validação a um conjunto de dados que é separado em uma solução de n-camadas é basicamente o mesmo que adicionar validação a um conjunto de dados de arquivo único (um conjunto de dados em um único projeto). É o local sugerido para executar a validação de dados durante o <xref:System.Data.DataTable.ColumnChanging> e/ou <xref:System.Data.DataTable.RowChanging> eventos de uma tabela de dados.

 O conjunto de dados fornece a funcionalidade para criar classes parciais para o qual você pode adicionar código de usuário para eventos de alteração de coluna e linha das tabelas de dados no conjunto de dados. Para obter mais informações sobre como adicionar código a um conjunto de dados em uma solução de n camadas, consulte [adicionar código a conjuntos de dados em aplicativos de n camadas](../data-tools/add-code-to-datasets-in-n-tier-applications.md), e [adicionar código a TableAdapters em aplicativos de n camadas](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Para obter mais informações sobre classes parciais, consulte [como: dividir uma classe em Classes parciais (Designer de classe)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) ou [Classes e métodos Partial](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

> [!NOTE]
>  Quando você separar datasets de TableAdapters (Configurando o **projeto DataSet** propriedade), classes parciais dataset existentes no projeto não ser movidas automaticamente. Classes parciais dataset existentes devem ser movidas manualmente para o projeto de conjunto de dados.

> [!NOTE]
>  O dataset Designer não cria automaticamente manipuladores de eventos em c# para o <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> eventos. Você precisa criar um manipulador de eventos manualmente e conectar o manipulador de eventos ao evento subjacente. Os procedimentos a seguir descrevem como criar manipuladores de eventos necessários no Visual Basic e c#.

## <a name="validate-changes-to-individual-columns"></a>Validar alterações em colunas individuais
 Valide valores em colunas individuais manipulando o <xref:System.Data.DataTable.ColumnChanging> evento. O <xref:System.Data.DataTable.ColumnChanging> é gerado quando um valor em uma coluna é modificado. Criar um manipulador de eventos para o <xref:System.Data.DataTable.ColumnChanging> eventos clicando duas vezes na coluna desejada no **Dataset Designer**.

 Na primeira vez, clique duas vezes em uma coluna, o designer gera um manipulador de eventos para o <xref:System.Data.DataTable.ColumnChanging> evento. Um `If...Then` instrução também é criada que testa a coluna específica. Por exemplo, o código a seguir é gerado quando você clicar duas vezes a coluna RequiredDate na tabela Orders do Northwind:

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
>  Em projetos c#, o Dataset Designer cria classes parciais somente para o conjunto de dados e tabelas individuais no conjunto de dados. O Designer de conjunto de dados não cria automaticamente manipuladores de eventos para o <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> eventos em c# como ele faz no Visual Basic. Em projetos c#, você precisa construir manualmente um método para manipular o evento e conectar-se com o método para o evento subjacente. O procedimento a seguir fornece as etapas para criar os manipuladores de eventos necessários no Visual Basic e c#.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Para adicionar validação durante alterações em valores de colunas individuais

1.  Abra o conjunto de dados clicando duas vezes o **. xsd** arquivo **Gerenciador de soluções**. Para obter mais informações, consulte [passo a passo: Criando um conjunto de dados no Designer de conjunto de dados](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Clique duas vezes a coluna que você deseja validar. Essa ação cria o <xref:System.Data.DataTable.ColumnChanging> manipulador de eventos.

    > [!NOTE]
    >  O Designer de conjunto de dados não cria automaticamente um manipulador de eventos para o evento de c#. O código que é necessário para manipular o evento em c# é incluído na próxima seção. `SampleColumnChangingEvent` é criado e, em seguida, conectado ao <xref:System.Data.DataTable.ColumnChanging> evento o <xref:System.Data.DataTable.EndInit%2A> método.

3.  Adicione código para verificar que `e.ProposedValue` contém dados que atenda aos requisitos do seu aplicativo. Se o valor proposto é inaceitável, defina a coluna para indicar que ela contém um erro.

     O exemplo de código a seguir valida que o **quantidade** coluna contém um valor maior que 0. Se **quantidade** é menor ou igual a 0, a coluna é definida como um erro. O `Else` cláusula limpa o erro se **quantidade** é maior que 0. O código no manipulador de eventos de alteração de coluna deve se parecer com o seguinte:

    ```vb
    If (e.Column.ColumnName = Me.QuantityColumn.ColumnName) Then
        If CType(e.ProposedValue, Short) <= 0 Then
            e.Row.SetColumnError(e.Column, "Quantity must be greater than 0")
        Else
            e.Row.SetColumnError(e.Column, "")
        End If
    End If
    ```
    ```csharp
    // Add this code to the DataTable partial class.

    public override void EndInit()
    {
        base.EndInit();
        // Hook up the ColumnChanging event
        // to call the SampleColumnChangingEvent method.
        ColumnChanging += SampleColumnChangingEvent;
    }

    public void SampleColumnChangingEvent(object sender, System.Data.DataColumnChangeEventArgs e)
    {
        if (e.Column.ColumnName == QuantityColumn.ColumnName)
        {
            if ((short)e.ProposedValue <= 0)
            {
                e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
            }
            else
            {
                e.Row.SetColumnError("Quantity", "");
            }
        }
    }
    ```

## <a name="validate-changes-to-whole-rows"></a>Validar alterações em linhas inteiras
 Valide valores em todas as linhas manipulando o <xref:System.Data.DataTable.RowChanging> evento. O <xref:System.Data.DataTable.RowChanging> é gerado quando os valores em todas as colunas são confirmados. É necessário validar no <xref:System.Data.DataTable.RowChanging> evento quando o valor em uma coluna depende do valor em outra coluna. Por exemplo, considere OrderDate e RequiredDate na tabela Orders na Northwind.

 Quando pedidos estão sendo inseridos, a validação certifica-se de que um pedido não é inserido com um RequiredDate que está em ou antes de OrderDate. Neste exemplo, os valores para colunas de RequiredDate e OrderDate precisam ser comparados, para que validar uma alteração de coluna individual não faz sentido.

 Criar um manipulador de eventos para o <xref:System.Data.DataTable.RowChanging> eventos clicando duas vezes o nome da tabela na barra de título da tabela no **Dataset Designer**.

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Para adicionar validação durante alterações em linhas inteiras

1.  Abra o conjunto de dados clicando duas vezes o **. xsd** arquivo **Gerenciador de soluções**. Para obter mais informações, consulte [passo a passo: Criando um conjunto de dados no Designer de conjunto de dados](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2.  Clique duas vezes na barra de título da tabela de dados no designer.

     Uma classe parcial é criada com um `RowChanging` manipulador de eventos e é aberto no Editor de códigos.

    > [!NOTE]
    >  O Designer de conjunto de dados não cria automaticamente um manipulador de eventos para o <xref:System.Data.DataTable.RowChanging> eventos em projetos c#. Você precisa criar um método para tratar o <xref:System.Data.DataTable.RowChanging> eventos e executar o código, em seguida, ligar o evento no método de inicialização da tabela.

3.  Adicione código de usuário dentro da declaração de classe parcial.

4.  O código a seguir mostra onde adicionar código de usuário para validar durante o <xref:System.Data.DataTable.RowChanging> evento. O exemplo c# também inclui um código para conectar-se com o método de manipulador de eventos até o `OrdersRowChanging` evento.

    ```vb
    Partial Class OrdersDataTable
        Private Sub OrdersDataTable_OrdersRowChanging(ByVal sender As System.Object, ByVal e As OrdersRowChangeEvent) Handles Me.OrdersRowChanging
            ' Add logic to validate columns here.
            If e.Row.RequiredDate <= e.Row.OrderDate Then
                ' Set the RowError if validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate"
            Else
                ' Clear the RowError when validation passes.
                e.Row.RowError = ""
            End If
        End Sub
    End Class
    ```
    ```csharp
    partial class OrdersDataTable
    {
        public override void EndInit()
        {
            base.EndInit();
            // Hook up the event to the
            // RowChangingEvent method.
            OrdersRowChanging += RowChangingEvent;
        }

        public void RowChangingEvent(object sender, OrdersRowChangeEvent e)
        {
            // Perform the validation logic.
            if (e.Row.RequiredDate <= e.Row.OrderDate)
            {
                // Set the row to an error when validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate";
            }
            else
            {
                // Clear the RowError if validation passes.
                e.Row.RowError = "";
            }
        }
    }
    ```

## <a name="see-also"></a>Consulte também

- [Visão geral de aplicativos de dados de N camadas](../data-tools/n-tier-data-applications-overview.md)
- [Passo a passo: criando um aplicativo de dados de N camadas](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Validando dados em conjuntos de dados](../data-tools/validate-data-in-datasets.md)