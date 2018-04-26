---
title: 'Como: alterar o tipo de retorno de um método DataContext (O R Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f4f1c9ffe0b9e6e7a112b50325e53955e5a97f01
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Como: alterar o tipo de retorno de um método DataContext (Object Relational Designer)
O tipo de retorno de um método de <xref:System.Data.Linq.DataContext> (criado com base em um procedimento ou uma função armazenadas) diferem dependendo de onde você ignora o procedimento ou a função em [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Se você soltar um item diretamente em uma classe existente de entidade, um método de <xref:System.Data.Linq.DataContext> que tem o tipo de retorno de classe de entidade é criado (se o esquema dos dados retornados por correspondências armazenadas do procedimento ou função a forma de classe de entidade). Se você soltar um item em uma área vazia de [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], um método de <xref:System.Data.Linq.DataContext> que retorna um tipo gerado automaticamente é criado. Você pode alterar o tipo de retorno de um método de <xref:System.Data.Linq.DataContext> depois de adicioná-lo ao painel de métodos. Para verificar ou alterar o tipo de retorno de um <xref:System.Data.Linq.DataContext> método, selecione-o e clique no **tipo de retorno** propriedade o **propriedades** janela.

> [!NOTE]
>  Não é possível reverter <xref:System.Data.Linq.DataContext> métodos que têm um tipo de retorno definido como uma classe de entidade para retornar o tipo gerado automaticamente usando o **propriedades** janela. Para reverter um método de <xref:System.Data.Linq.DataContext> para retornar um tipo gerado automaticamente, você deve arraste o objeto de base de dados original em object relational Designer de Objetos novamente.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Para alterar o tipo de retorno de um método DataContext do tipo gerado automaticamente a uma entidade

1.  Selecione o método de <xref:System.Data.Linq.DataContext> no painel de métodos.

2.  Selecione **tipo de retorno** no **propriedades** janela e, em seguida, selecione uma entidade disponível classe no **tipo de retorno** lista. Se a classe da entidade desejada não estiver na lista, adicioná-lo ou criá-la no [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] para adicioná-lo à lista.

3.  Salve o arquivo. dbml.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Para alterar o tipo de retorno de um método DataContext de uma classe de entidade de volta para o tipo gerado automaticamente

1.  Selecione o método de <xref:System.Data.Linq.DataContext> no painel de métodos e exclua-o.

2.  Arraste o objeto de banco de dados da **Server Explorer**/**Pesquisador de objetos de banco de dados** em uma área vazia do / R Designer.

3.  Salve o arquivo. dbml.

## <a name="see-also"></a>Consulte também

- [Ferramentas LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Métodos de DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Como: criar métodos DataContext mapeados para procedimentos armazenados e funções (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)