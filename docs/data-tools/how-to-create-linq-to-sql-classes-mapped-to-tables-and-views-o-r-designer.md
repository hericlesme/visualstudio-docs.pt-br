---
title: 'Como: criar LINQ para classes SQL mapeadas para tabelas e exibições (O R Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0b81d67d6897826ab2f6de1e3b48663b18bffdb1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924629"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Como: criar LINQ para classes SQL mapeadas para tabelas e exibições (Object Relational Designer)
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] classes que são mapeados para tabelas de banco de dados e modos de exibição são chamados *classes de entidade*. A classe da entidade é mapeado para um registro, enquanto as propriedades individuais de uma classe de entidade mapeiam para as colunas individuais que compõem um registro. Criar classes de entidade com base em tabelas de banco de dados ou exibições arrastando tabelas ou exibições do **Server Explorer**/**Pesquisador de objetos de banco de dados** até o [LINQ to SQL Tools no O Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). O [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] gera as classes e se aplica a específica [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] atributos para habilitar [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] funcionalidade (a comunicação de dados e recursos de edição a <xref:System.Data.Linq.DataContext>). Para obter informações detalhadas sobre [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] classes, consulte [o LINQ no modelo de objeto do SQL](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).

> [!NOTE]
>  O [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] é um mapeador relacional de objeto simples, pois suporta apenas a relações do mapeamento 1:1. Em outras palavras, uma classe de entidade pode ter apenas uma relação de mapeamento de 1:1 com uma tabela ou exibição de banco de dados. O mapeamento complexo, como o mapeamento de uma classe de entidade para várias tabelas, não tem suporte. No entanto, você pode mapear uma classe de entidade para uma exibição que une várias tabelas relacionadas.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Criar classes LINQ to SQL que são mapeadas para tabelas ou exibições de banco de dados
 Arrastando tabelas ou exibições de **Server Explorer**/**Pesquisador de objetos de banco de dados** para o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] cria classes de entidade, além de <xref:System.Data.Linq.DataContext> métodos que são usados para executando atualizações.

 Por padrão, o tempo de execução do [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] cria a lógica para salvar alterações de uma classe de entidade atualizável de volta para o banco de dados. Essa lógica é baseada no esquema da tabela (as definições de coluna e informações de chave primária). Se você não quiser esse comportamento, poderá configurar uma classe de entidade para usar os procedimentos armazenados para executar inserções, atualizações e exclusões, em vez de usar o comportamento padrão de tempo de execução do [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]. Para obter mais informações, consulte [como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Para criar classes LINQ to SQL que são mapeadas para tabelas ou exibições de banco de dados

1.  Em **servidor**/**Pesquisador de objetos de banco de dados**, expanda **tabelas** ou **exibições** e localize a tabela de banco de dados ou exibição que você deseja Para usar em seu aplicativo.

2.  Arraste a tabela ou exibição para o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

     Uma classe de entidade é criada e aparece na superfície de design. A classe de entidade tem propriedades que mapeiam para as colunas na tabela ou exibição selecionada.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Crie um objeto de fonte de dados e exiba os dados em um formulário
 Depois de criar classes de entidade usando o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], você pode criar um objeto de fonte de dados e popular a [janela fontes de dados](add-new-data-sources.md) com as classes de entidade.

#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Para criar uma fonte de dados de objeto com base nas classes de entidade do LINQ to SQL

1.  Sobre o **criar** menu, clique em **compilar solução** para compilar o projeto.

2.  Sobre o **dados** menu, clique em **Mostrar fontes de dados**.

3.  No **fontes de dados** janela, clique em **adicionar nova fonte de dados**.

4.  Clique em **objeto** no **escolher um tipo de fonte de dados** página e, em seguida, clique em **próximo**.

5.  Expanda os nós e localize e selecione sua classe.

    > [!NOTE]
    >  Se o **cliente** classe não está disponível, cancele o assistente, compile o projeto e execute o assistente novamente.

6.  Clique em **concluir** para criar a fonte de dados e adicionar o **cliente** classe da entidade para o **fontes de dados** janela.

7.  Arraste itens do **fontes de dados** janela em um formulário.

## <a name="see-also"></a>Consulte também

- [Ferramentas LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Passo a passo: Criando Classes LINQ to SQL (O R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Métodos de DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Como: criar métodos DataContext mapeados para procedimentos armazenados e funções (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [O modelo de objeto LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [Passo a passo: personalizando a inserção, a atualização e o comportamento de exclusão de classes de entidade](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Como: criar uma associação (relação) entre classes LINQ to SQL (Object Relational Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)