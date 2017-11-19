---
title: "A classe selecionada não pode ser excluída porque ele é usado como um tipo de retorno para um ou mais métodos DataContext | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 865c8f9fa91c24eed1e10bde68b239932237a62b
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2017
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>A classe selecionada não pode ser excluída porque é usada como um tipo de retorno para um ou mais métodos DataContext
O tipo de retorno de um ou mais métodos de <xref:System.Data.Linq.DataContext> é a classe de entidade selecionada. Excluindo um classe de entidade que é usada como o tipo de retorno para um método de <xref:System.Data.Linq.DataContext> fará com que a compilação do projeto falhar. Para excluir a classe selecionada de entidade, identifica os métodos de <xref:System.Data.Linq.DataContext> que a usam e definem seus tipos de retorno para uma classe diferente de entidade.  
  
 Para reverter os tipos de retorno de <xref:System.Data.Linq.DataContext> métodos para seus tipos originais gerado automaticamente, primeiro exclua o <xref:System.Data.Linq.DataContext> método do painel de métodos e, em seguida, arraste o objeto da **Server Explorer** / **Pesquisador de objetos de banco de dados** para Object Relational Designer novamente.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Identificar <xref:System.Data.Linq.DataContext> métodos que usam a classe de entidade como um tipo de retorno, selecionando um <xref:System.Data.Linq.DataContext> método nos métodos de painel e inspecionando o **tipo de retorno** propriedade o **propriedades** janela .  
  
2.  Definir o **tipo de retorno** para uma classe de entidade diferente ou exclua o <xref:System.Data.Linq.DataContext> método do painel de métodos.  
  
## <a name="see-also"></a>Consulte também
[Mensagens de Object Relational Designer](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)