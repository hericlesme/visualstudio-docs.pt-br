---
title: Este método relacionado é o método de suporte para a seguir inserção, atualização, ou métodos padrão de exclusão
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: fdb359ebe4a42e0ddad8b93c1e746922ac609f60
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31922477"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Este método relacionado é o método de suporte para a seguir inserção, atualização, ou métodos padrão de exclusão

Este método relacionado é o método de suporte para a seguir inserção, atualização, ou métodos padrão de exclusão. Se ele for excluído, esses métodos também serão excluídos. Deseja continuar?

O método selecionado de `DataContext` é usado atualmente como um dos métodos insert, update, ou DELETE para uma das classes de entidade em object relational Designer de Objetos. Exclua o método selecionado fará com que a classe de entidade que estiver usando esse método para reverter para o comportamento padrão de tempo de execução para executar a inserção, atualização ou exclusão, durante uma atualização.

## <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Para excluir o método selecionado, causando a classe de entidade às atualizações de uso

- Clique em **Sim**.

    O método selecionado é excluído e as classes que usam esse método substituindo o comportamento de atualização são revertidas para usar o comportamento padrão de tempo de execução LINQ to SQL.

## <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Para fechar a caixa de mensagem, deixando o método selecionado inalterado

- Clique em **Não**.

    A caixa de mensagem fecha e nenhuma alteração é feita.

## <a name="see-also"></a>Consulte também

- [Mensagens do O/R Designer](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)