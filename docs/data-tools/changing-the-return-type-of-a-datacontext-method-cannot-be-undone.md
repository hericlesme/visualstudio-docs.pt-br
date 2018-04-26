---
title: Altere o tipo de retorno de um método DataContext não pode ser desfeito
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 40c68aba0599f2f86285cbea841d06f0a652828a
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>Altere o tipo de retorno de um método DataContext não pode ser desfeito

A alteração do tipo retornado por um método DataContext não pode ser desfeita. Para reverter de volta para o tipo gerado automaticamente, você deve arraste o item do Gerenciador de Servidores/Gerenciador de Base de dados em object relational Designer de Objetos novamente. Tem certeza de que deseja alterar o tipo retornado?

O tipo de retorno de um método de <xref:System.Data.Linq.DataContext> diferem dependendo de onde você ignora o item em [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Se você soltar um item diretamente em uma classe existente de entidade, um método de <xref:System.Data.Linq.DataContext> que tem o tipo de retorno de classe de entidade é criado. Se você soltar um item em uma área vazia de [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], um método de <xref:System.Data.Linq.DataContext> que retorna um tipo gerado automaticamente é criado. Você pode alterar o tipo de retorno de um método de <xref:System.Data.Linq.DataContext> depois de adicioná-lo ao painel de métodos. Para verificar ou alterar o tipo de retorno de um <xref:System.Data.Linq.DataContext> método, selecione-o e clique no **tipo de retorno** propriedade o **propriedades** janela.

## <a name="to-change-the-return-type-of-a-datacontext"></a>Para alterar o tipo de retorno de um DataContext

- Clique em **Sim**.

## <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>Para sair da caixa de mensagem e deixar o tipo de retorno inalterado

- Clique em **Não**.

## <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Para reverter para o tipo de retorno original após alterar o tipo de retorno

1. Selecione o <xref:System.Data.Linq.DataContext> método sobre o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] e excluí-lo.

2. Localize o item em **Server Explorer/Database Explorer** e arraste-a para o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

    Um método de <xref:System.Data.Linq.DataContext> é criado com o tipo de retorno padrão original.

## <a name="see-also"></a>Consulte também

- [Mensagens do O/R Designer](../data-tools/o-r-designer-messages.md)
- [LINQ to SQL tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)