---
title: "Não é possível atribuir a &#39; isso &#39; | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c164b9b7d2989076a9dc0ef0bafba6159bc08885
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="cannot-assign-to-39this39"></a>Não é possível atribuir a &#39; isso &#39;
Você tentou atribuir um valor para **isso**. **Isso** é um [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] palavra-chave que se refere a um:  
  
-   o objeto de um método, em execução atualmente  
  
-   o objeto global, se não há nenhum método atual (ou o método não pertence a nenhum outro objeto).  
  
 Um método é um [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] função que é chamada por meio de um objeto. Dentro de um método, o **isso** palavra-chave é uma referência ao objeto que o método é invocado por meio de (que é o objeto criado chamando o construtor de classe com o **novo** operador).  
  
 Dentro de um método, você pode usar **isso** fazer referência ao objeto atual, mas não é possível atribuir um novo valor para **isso**.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Não tente atribuir a **isso**. Para acessar uma propriedade ou método de um objeto instanciado, use o operador ponto (por exemplo, círculo**.** RADIUS).  
  
    > [!NOTE]
    >  Não é possível nomear uma variável de usuário criado **isso**; é um [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] palavra reservada.  
  
## <a name="see-also"></a>Consulte também  
 [Essa instrução](../../javascript/reference/this-statement-javascript.md)   
 [Solucionar problemas com scripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)