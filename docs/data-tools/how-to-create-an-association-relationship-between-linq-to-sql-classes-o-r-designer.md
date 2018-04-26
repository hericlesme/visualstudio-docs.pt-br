---
title: Como criar uma relação entre classes LINQ to SQL usando o O/R Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1fee78966a04da53e3b61b85a3440ea8e459771d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-an-association-between-linq-to-sql-classes-or-designer"></a>Como: criar uma associação entre classes LINQ to SQL (Object Relational Designer)
As associações entre classes de entidade no [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] são análogas às relações entre tabelas em um banco de dados. Você pode criar associações entre classes de entidade usando o **Editor de associação** caixa de diálogo.

Você deve selecionar uma classe pai e filho, quando você usa o **Editor de associação** caixa de diálogo para criar uma associação. A classe pai é a classe de entidade que contém a chave primária; a classe filho é a classe de entidade que contém a chave estrangeira. Por exemplo, se as classes de entidade foram criadas que mapeiam para as tabelas Customers e Orders do Northwind, a classe Customer seria a classe pai e a classe Order seria a classe filho.

> [!NOTE]
>  Quando você arrasta a tabelas de **Server Explorer**/**Pesquisador de objetos de banco de dados** até o [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]), associações são criadas automaticamente com base em existente relações de chave estrangeira no banco de dados.

## <a name="association-properties"></a>Propriedades de associação
Depois de criar uma associação, quando você seleciona a associação no Object Relational Designer, há algumas propriedades configuráveis a **propriedades** janela. (A associação é a linha entre as classes relacionadas.) A tabela a seguir fornece descrições para as propriedades de uma associação.

|Propriedade|Descrição|
|--------------|-----------------|
|**Cardinalidade**|Controla se a associação é de um-para-muitos ou um-para-um.|
|**Propriedade filho**|Especifica se deve ser criada uma propriedade no pai que é uma coleção ou referência para os registros filho na parte da chave estrangeira da associação. Por exemplo, na associação entre Customer e Order, se o **propriedade filho** é definido como **True**, uma propriedade chamada Orders é criada na classe pai.|
|**Propriedade pai**|A propriedade na classe filho que referencia a classe pai associada. Por exemplo, na associação entre Customer e Order, uma propriedade chamada Customer que referencia o cliente associado para um pedido é criada na classe Order.|
|**Propriedades participantes**|Exibe as propriedades de associação e fornece um **reticências** botão (…) que abre novamente o **Editor de associação** caixa de diálogo.|
|**Exclusivo**|Especifica se as colunas de destino estrangeiras têm uma restrição de exclusividade.|

## <a name="to-create-an-association-between-entity-classes"></a>Para criar uma associação entre classes de entidade

1.  A classe de entidade que representa a classe pai na associação de atalho, aponte para **adicionar**e, em seguida, clique em **associação**.

2.  Verifique o correto **classe pai** está selecionado no **Editor de associação** caixa de diálogo.

3.  Selecione o **classe filho** na caixa de combinação.

4.  Selecione o **propriedades de associação** que se relacionam as classes. Geralmente, isso mapeia para a relação de chave estrangeira definida no banco de dados. Por exemplo, na associação Customers e Orders, o **propriedades de associação** são CustomerID para cada classe.

5.  Clique em **Okey** para criar a associação.

## <a name="see-also"></a>Consulte também

- [Ferramentas LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Passo a passo: Criando Classes LINQ to SQL](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Métodos de DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Como representar chaves primárias](/dotnet/framework/data/adonet/sql/linq/how-to-represent-primary-keys)