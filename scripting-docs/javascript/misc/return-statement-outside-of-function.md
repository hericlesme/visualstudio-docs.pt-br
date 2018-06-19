---
title: '&#39; retorno &#39; instrução fora da função | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07b633c87dc11b291a5a5783f8121b2a368996d6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633506"
---
# <a name="39return39-statement-outside-of-function"></a>&#39; retorno &#39; instrução fora da função
Você usou um `return` instrução no escopo global do seu código. O `return` instrução só deve aparecer dentro do corpo de uma função.  
  
 Invocar uma função com o `()` operador é uma expressão. Todas as expressões têm valores; o `return` instrução é usada para especificar o valor reajustado por uma função. O formato geral é:  
  
```  
  
return [ expression ];  
```  
  
 Quando o `return` instrução é executada, *expressão* é avaliado e retornado como o valor da função. Se não houver nenhuma expressão **indefinido** é retornado.  
  
 A execução da função para quando o `return` instrução é executada, mesmo se não houver outras instruções restantes ainda no corpo da função. A exceção a essa regra é se o **retornar** instrução ocorre dentro de um **tente** bloco, e há um correspondente **finalmente** bloco, o código no  **Por fim** bloco será executado antes da função retorna.  
  
 Se uma função retorna porque ele atinge o final do corpo da função sem executar uma `return` instrução, o valor retornado é o **indefinido** valor (Isso significa que o resultado da função não pode ser usado como parte de uma expressão maior ).  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Remover o `return` instrução do corpo principal do seu código (o escopo global).  
  
## <a name="see-also"></a>Consulte também  
 [Instrução return](../../javascript/reference/return-statement-javascript.md)   
 [Objeto de função](../../javascript/reference/function-object-javascript.md)   
 [Propriedade caller (Function)](../../javascript/reference/caller-property-function-javascript.md)