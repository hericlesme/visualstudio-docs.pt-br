---
title: 'Como: criar LINQ to SQL classes mapeadas para tabelas e exibições (Object Relational Designer)'
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
ms.openlocfilehash: 11fb4265047387e30327bbbe17c9babf1f23ec61
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089319"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Como: criar LINQ to SQL classes mapeadas para tabelas e exibições (Designer relacional de objetos)
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] são chamadas de classes que são mapeadas para tabelas de banco de dados e exibições *classes de entidade*. A classe de entidade é mapeado para um registro, enquanto as propriedades individuais de uma classe de entidade mapeiam para as colunas individuais que compõem um registro. Criar classes de entidade que se baseiam no banco de dados tabelas ou exibições arrastando tabelas ou exibições do **Gerenciador de servidores** ou **Database Explorer** até o [LINQ to SQL das ferramentas no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). O **Relational Designer** gera as classes e aplica o específico [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] para habilitar [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] funcionalidade (a comunicação de dados e recursos de edição a <xref:System.Data.Linq.DataContext>). Para obter informações detalhadas sobre [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] classes, consulte [o LINQ no modelo de objeto do SQL](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).

> [!NOTE]
>  O **Relational Designer** é um mapeador relacional de objeto simples, pois suporta apenas as relações de mapeamento de 1:1. Em outras palavras, uma classe de entidade pode ter apenas uma relação de mapeamento de 1:1 com uma tabela ou exibição de banco de dados. O mapeamento complexo, como o mapeamento de uma classe de entidade para várias tabelas, não tem suporte. No entanto, você pode mapear uma classe de entidade para uma exibição que une várias tabelas relacionadas.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Criar LINQ to SQL classes que são mapeadas para tabelas de banco de dados ou exibições
 Arrastar tabelas ou exibições do **Gerenciador de servidores** ou **Database Explorer** até o **Relational Designer** cria classes de entidade além o <xref:System.Data.Linq.DataContext> métodos que são usados para realizar atualizações.

 Por padrão, o tempo de execução do [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] cria a lógica para salvar alterações de uma classe de entidade atualizável de volta para o banco de dados. Essa lógica é baseada no esquema da tabela (as definições de coluna e informações de chave primária). Se você não quiser esse comportamento, você pode configurar uma classe de entidade para usar procedimentos armazenados para executar inserções, atualizações e exclusões em vez de usar o padrão [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] comportamento de tempo de execução. Para obter mais informações, consulte [como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer relacional de objetos)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Para criar classes LINQ to SQL que são mapeadas para tabelas ou exibições de banco de dados

1.  Na **Server** ou **Database Explorer**, expanda **tabelas** ou **exibições** e localize a tabela de banco de dados ou exibição a que você deseja usar no seu aplicativo.

2.  Arraste a tabela ou exibição para o **Relational Designer**.

     Uma classe de entidade é criada e aparece na superfície de design. A classe de entidade tem propriedades que mapeiam para as colunas na tabela ou exibição selecionada.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Criar uma fonte de dados de objeto e exibir os dados em um formulário
 Depois de criar classes de entidade usando o **Relational Designer**, você pode criar uma fonte de dados de objeto e preencher o [janela Data Sources](add-new-data-sources.md) com as classes de entidade.

### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Para criar uma fonte de dados de objeto com base nas classes de entidade do LINQ to SQL

1.  Sobre o **Build** menu, clique em **compilar solução** para compilar seu projeto.

2.  Sobre o **dados** menu, clique em **Show Data Sources**.

3.  No **fontes de dados** janela, clique em **Add New Data Source**.

4.  Clique em **objeto** sobre o **escolher um tipo de fonte de dados** página e, em seguida, clique em **próxima**.

5.  Expanda os nós e localize e selecione sua classe.

    > [!NOTE]
    >  Se o **cliente** classe não estiver disponível, cancele o assistente, compile o projeto e execute o assistente novamente.

6.  Clique em **terminar** para criar a fonte de dados e adicionar o **Customer** classe de entidade para o **fontes de dados** janela.

7.  Arraste itens dos **fontes de dados** janela em um formulário.

## <a name="see-also"></a>Consulte também

- [Ferramentas LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Passo a passo: Criando o LINQ para SQL classes (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Métodos de DataContext (Designer relacional de objetos)](../data-tools/datacontext-methods-o-r-designer.md)
- [Como: criar métodos DataContext mapeados para procedimentos armazenados e funções (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [O LINQ no modelo de objeto do SQL](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)
- [Passo a passo: personalizando a inserção, a atualização e o comportamento de exclusão de classes de entidade](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Como: criar uma associação (relação) entre classes LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)