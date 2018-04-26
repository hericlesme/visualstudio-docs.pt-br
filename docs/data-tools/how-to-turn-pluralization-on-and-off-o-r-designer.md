---
title: 'Como: ative em pluralization e off (O R Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a8c477ac276ce0ff9c292dc42ba2f5f7d1e53dd9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Como: ative em pluralization e off (Object Relational Designer)
Por padrão, quando você arrastar objetos de banco de dados que têm nomes que terminam em s ou propriedades de **Server Explorer**/**Pesquisador de objetos de banco de dados** até o [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), os nomes das classes de entidades geradas são alterados de plural a forma singular. Isso é feito a representa mais precisamente o fato que a classe instanciado de entidade mapeia para um único registro de dados. Por exemplo, adicione uma tabela de clientes para os resultados de [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] em uma classe de entidade chamada Cliente porque a classe conterá dados para apenas um único cliente.

> [!NOTE]
>  Pluralization está ativada por padrão somente na versão de língua inglesa do Visual Studio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Para desativar o pluralization e sobre

1.  No menu **Ferramentas**, clique em **Opções**.

2.  No **opções** caixa de diálogo caixa, expanda **ferramentas de banco de dados**.

    > [!NOTE]
    >  Selecione **Mostrar todas as configurações** se o **ferramentas de banco de dados** nó não está visível.

3.  Clique em **Object Relational Designer**.

4.  Definir **Pluralização de nomes de** para **habilitado** = **False** para definir o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] para que ele não altera os nomes de classe.

5.  Definir **Pluralização de nomes de** para **habilitado** = **True** para aplicar regras de pluralização para os nomes de classe de objetos adicionados ao [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

## <a name="see-also"></a>Consulte também

- [Ferramentas LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)