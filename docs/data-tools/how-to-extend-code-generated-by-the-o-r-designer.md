---
title: 'Como: estender o código gerado pelo Designer O R'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 0210037cdd554838c9fe08c424f02b081c6f2e1a
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Como: Estender o código gerado por object relational Designer de Objetos
O código gerado por [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] é regenerado quando alterações são feitas a classes de entidade e outros objetos ocorrem no designer. Devido a essa regeneração de código, qualquer código que você adicionar ao código gerado seja substituído normalmente quando o código de regenerados de designer. [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] fornece a capacidade de gerar os arquivos parciais da classe em que você pode adicionar código que não será substituído. Um exemplo de adicionar seu próprio código para o código gerado por [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] está adicionando validação de dados para as classes LINQ to SQL (entidade). Para obter informações, consulte [como: adicionar validação a classes de entidade](../data-tools/how-to-add-validation-to-entity-classes.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="adding-code-to-an-entity-class"></a>Adicionando código para uma classe de entidade

#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Para criar uma classe parcial e adicione o código para uma classe de entidade

1.  Abra ou crie um novo arquivo LINQ to SQL Classes (**dbml** arquivo) no [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. (Clique duas vezes o **dbml** arquivo **Solution Explorer**/**Pesquisador de objetos de banco de dados**.)

2.  No [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], clique com botão direito a classe para a qual você deseja adicionar validação e, em seguida, clique em **Exibir código**.

     O editor de códigos abre com uma classe parcial para a classe de entidade selecionada.

3.  Adicione o código na declaração de classe parcial para a classe de entidade.

## <a name="adding-code-to-a-datacontext"></a>Adicionando código para um DataContext

#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Para criar uma classe parcial e adicione o código a um DataContext

1.  Abra ou crie um novo arquivo LINQ to SQL Classes (**dbml** arquivo) no [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. (Clique duas vezes o **dbml** arquivo **Solution Explorer**/**Pesquisador de objetos de banco de dados**.)

2.  No [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], clique em uma área vazia no designer e, em seguida, clique em **Exibir código**.

     O editor de códigos abre com uma classe parcial para o DataContext.

3.  Adicione o código na declaração de classe parcial para o DataContext.

## <a name="see-also"></a>Consulte também

- [Ferramentas LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Passo a passo: Criando Classes LINQ to SQL (O R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)