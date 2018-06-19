---
title: 'Como: adicionar validação a classes de entidade'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 46eb04100f455bbd1d8dc26ad2b7c1a67e2da50d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31923119"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Como: adicionar validação a classes de entidade
*Validando* classes de entidade é o processo de confirmar que os valores inseridos em objetos de dados estão em conformidade com as restrições no esquema de um objeto e também as regras estabelecidas para o aplicativo. Validar dados antes de enviar atualizações para o base de dados subjacente é uma boa prática que reduz erros. Também reduz o número potencial de processamentos entre um aplicativo e o base de dados.

 O [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fornece os métodos parciais que permitem aos usuários estender o código gerado pelo designer que é executada durante inserções, atualizações e exclusões de entidades completas e também durante e após a coluna individual alterações.

> [!NOTE]
>  Este tópico fornece as etapas básicas para adicionar validação a classes de entidade usando [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Porque ele pode ser difícil de seguir essas etapas genéricas sem fazer referência a uma classe de entidade específica, foi fornecida um passo a passo que usa dados reais.

## <a name="adding-validation-for-changes-to-the-value-in-a-specific-column"></a>Adicionar validação para alterações ao valor em uma coluna específica
 Este procedimento mostra como validar dados quando o valor em uma coluna é alterado. Porque a validação é executada dentro da definição de classe (em vez de na interface do usuário) será lançada uma exceção se o valor faz com que a validação falhar. Implementar manipulação de erro para o código em seu aplicativo que tenta alterar os valores de coluna.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-validate-data-during-a-columns-value-change"></a>Para validar dados durante o valor de uma coluna alterar

1.  Abra ou crie um novo arquivo LINQ to SQL Classes (**dbml** arquivo) no [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. (Clique duas vezes o **dbml** arquivo **Solution Explorer**.)

2.  No Object Relational Designer, clique a classe para a qual você deseja adicionar validação e, em seguida, clique em **Exibir código**.

     O editor de códigos abre com uma classe parcial para a classe de entidade selecionada.

3.  Coloque o cursor na classe parcial.

4.  Para projetos do Visual Basic:

    1.  Expanda o **nome do método** lista.

    2.  Localize o **OnCOLUMNNAMEChanging** método para a coluna que você deseja adicionar a validação.

    3.  Um `OnCOLUMNNAMEChanging` método é adicionado à classe parcial.

    4.  Adicione o seguinte código para primeiro verificar que um valor está inserido e para garantir em que o valor inserido para a coluna é aceitável para seu aplicativo. O argumento de `value` contém o valor proposto, para adicionar a lógica para confirmar que é um valor válido:

        ```vb
        If value.HasValue Then
            ' Add code to ensure that the value is acceptable.
            ' If value < 1 Then
            '    Throw New Exception("Invalid data!")
            ' End If
        End If
        ```

    Para projetos C#:

    Como projetos c# não gerar automaticamente manipuladores de eventos, você pode usar o IntelliSense para criar os métodos parciais de alteração de coluna. Tipo `partial` e um espaço para acessar a lista de métodos parciais disponíveis. Clique no método de alteração para a coluna que você deseja adicionar validação para. O código a seguir é semelhante ao código que é gerado quando você seleciona um método parcial de alteração de coluna:

    ```csharp
    partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)
        {
           throw new System.NotImplementedException();
        }
    ```

## <a name="adding-validation-for-updates-to-an-entity-class"></a>Adicionar validação para atualizações para uma classe de entidade
 Além de verificar valores alterações pendentes, você também pode validar dados quando é feita uma tentativa de atualizar uma classe completa de entidade. A validação durante uma atualização tentada permite que você comparar valores em várias colunas se as regras comerciais exigem esta. O procedimento a seguir mostra como validar quando é feita uma tentativa de atualizar uma classe completa de entidade.

> [!NOTE]
>  O código de validação para que as atualizações terminem classes de entidade é executado na classe parcial de <xref:System.Data.Linq.DataContext> (em vez de na classe parcial de uma classe específica de entidade).

#### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Para validar dados durante uma atualização para uma entidade

1.  Abra ou crie um novo arquivo LINQ to SQL Classes (**dbml** arquivo) no [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. (Clique duas vezes o **dbml** arquivo **Solution Explorer**.)

2.  Clique em uma área vazia na Object Relational Designer e clique em **Exibir código**.

     O editor de códigos abre com uma classe parcial para `DataContext`.

3.  Coloque o cursor na classe parcial para `DataContext`.

4.  Para projetos do Visual Basic:

    1.  Expanda o **nome do método** lista.

    2.  Clique em **UpdateENTITYCLASSNAME**.

    3.  Um `UpdateENTITYCLASSNAME` método é adicionado à classe parcial.

    4.  Acessar valores de colunas individuais usando o argumento de `instance` , conforme mostrado no código o seguir:

        ```vb
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then
            Dim ErrorMessage As String = "Invalid data!"
            Throw New Exception(ErrorMessage)
        End If
        ```

    Para projetos C#:

    Como projetos c# não geram automaticamente manipuladores de eventos, você pode usar o IntelliSense para criar o parcial `UpdateCLASSNAME` método. Tipo `partial` e um espaço para acessar a lista de métodos parciais disponíveis. Clique no método de atualização para a classe que você deseja adicionar validação para. O código a seguir é semelhante ao código que é gerado quando você seleciona um `UpdateCLASSNAME` método parcial:

    ```csharp
    partial void UpdateCLASSNAME(CLASSNAME instance)
    {
        if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))
        {
            string ErrorMessage = "Invalid data!";
            throw new System.Exception(ErrorMessage);
        }
    }
    ```

## <a name="see-also"></a>Consulte também

- [Ferramentas LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Validando dados](../data-tools/validate-data-in-datasets.md)
- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)