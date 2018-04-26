---
title: 'Como: criar métodos DataContext mapeados para procedimentos armazenados e funções (O R Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ffec139089f77a1d5c3ffd855e16f12b31e35c17
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Como: criar métodos DataContext mapeados para procedimentos armazenados e funções (Object Relational Designer)
Procedimentos armazenados e funções podem ser adicionadas para o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] como <xref:System.Data.Linq.DataContext> métodos. Chamar o método e passar os parâmetros necessários executa a função ou procedimento armazenado no banco de dados e retorna os dados no tipo de retorno de <xref:System.Data.Linq.DataContext> método. Para obter informações detalhadas sobre <xref:System.Data.Linq.DataContext> métodos, consulte [métodos DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
>  Os procedimentos armazenados também podem ser usados para substituir o comportamento padrão em tempo de execução de [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] que executa inserções, atualizações e exclusões quando alterações são salvas de classes de entidade para um banco de dados. Para obter mais informações, consulte [como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="creating-datacontext-methods"></a>Criando métodos DataContext
 Você pode criar <xref:System.Data.Linq.DataContext> métodos arrastando procedimentos armazenados ou funções de **Server Explorer/Database Explorer** até o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

> [!NOTE]
>  O tipo de retorno do método <xref:System.Data.Linq.DataContext> gerado varia de acordo com o local onde você solta o procedimento armazenado ou a função no [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Soltar itens diretamente em uma classe de entidade existente cria um método <xref:System.Data.Linq.DataContext> com o tipo de retorno da classe de entidade. Soltar itens em uma área vazia do [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] cria um método <xref:System.Data.Linq.DataContext> que retorna um tipo gerado automaticamente. Você pode alterar o tipo de retorno de um <xref:System.Data.Linq.DataContext> método após adicioná-lo para o painel de métodos. Para verificar ou alterar o tipo de retorno de um <xref:System.Data.Linq.DataContext> método, selecione-o e inspecione o **tipo de retorno** propriedade no **propriedades** janela. Para obter mais informações, consulte [como: alterar o tipo de retorno de um método DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Para criar métodos DataContext que retornam tipos gerados automaticamente

1.  Em **Server Explorer**/**Pesquisador de objetos de banco de dados**, expanda o **procedimentos armazenados** nó do banco de dados que você está trabalhando.

2.  Localize o procedimento armazenado desejado e arraste-o para uma área vazia do [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

     O <xref:System.Data.Linq.DataContext> método é criado com um tipo de retorno gerado automaticamente e aparece no **métodos** painel.

#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Para criar métodos DataContext com o tipo de retorno de uma classe de entidade

1.  Em **Server Explorer**/**Pesquisador de objetos de banco de dados**, expanda o **procedimentos armazenados** nó do banco de dados que você está trabalhando.

2.  Localize o procedimento armazenado desejado e arraste-o para uma classe de entidade existente no [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

     O <xref:System.Data.Linq.DataContext> método é criado com o tipo de retorno da classe da entidade selecionada e aparece no **métodos** painel.

> [!NOTE]
>  Para obter informações sobre como alterar o tipo de retorno de existentes <xref:System.Data.Linq.DataContext> métodos, consulte [como: alterar o tipo de retorno de um método DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>Consulte também

- [Ferramentas LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Métodos de DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Passo a passo: Criando Classes LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Introdução ao LINQ no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
- [LINQ em C#](/dotnet/csharp/linq/linq-in-csharp)