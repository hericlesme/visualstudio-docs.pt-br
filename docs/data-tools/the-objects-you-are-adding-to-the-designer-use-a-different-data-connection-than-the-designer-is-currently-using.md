---
title: "Os objetos que você está adicionando ao designer de usam uma conexão de dados diferentes, o designer está usando atualmente | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: cb6b3e747db497b80893f271c97bb0f6d8c86894
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2017
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>Os objetos você estiver adicionando ao uso de designer uma conexão de dados diferente do designer está usando atualmente
Os objetos que você está adicionando ao designer usam uma conexão de dados diferente da que o designer está usando no momento. Deseja substituir a conexão usada pelo designer?  
  
 Para adicionar itens para o [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]), todos os itens de usam uma conexão de dados compartilhada. (A superfície de design representa <xref:System.Data.Linq.DataContext>, que usa uma única conexão para todos os objetos na superfície.) Se você adicionar um objeto para o designer que usa uma conexão de dados que seja diferente de conexão de dados atualmente sendo usada pelo designer, esta mensagem aparece. Para resolver esse erro, você pode escolher para manter a conexão existente. Se você fizer essa opção, o objeto selecionado não será adicionado. Como alternativa, você pode optar por adicionar o objeto e redefinir a <xref:System.Data.Linq.DataContext> conexão para a nova conexão.  
  
> [!NOTE]
>  Se você clicar em **Sim**, entidade todas as classes no [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] são mapeadas para a nova conexão.  
  
### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>Para substituir a conexão existente com a conexão usada pelo objeto selecionado  
  
-   Clique em **Sim**.  
  
     O objeto selecionado é adicionado a [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], e o DataContext.Connection é definido para a nova conexão.  
  
### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>Para continuar a usar a conexão e cancelar existentes que adicionam o objeto selecionado  
  
-   Clique em **Não**.  
  
     A ação é cancelada. O DataContext.Connection de definidas para a conexão existente.  
  
## <a name="see-also"></a>Consulte também
[Mensagens de Object Relational Designer](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
 