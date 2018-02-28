---
title: "Operador AND lógico (&amp;&amp;) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '&&'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- logical AND operator
- '&& operator'
ms.assetid: 4714dea9-1999-444a-8acd-72f0851e4f65
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2107eb89c5ca964cf08172050b49307cb150590f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="logical-and-operator-ampamp-javascript"></a>Operador AND lógico (&amp;&amp;) (JavaScript)
Executa uma conjunção lógica em duas expressões.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result = expression1 && expression2   
```  
  
## <a name="parameters"></a>Parâmetros  
 `result`  
 Qualquer variável.  
  
 `expression1`  
 Qualquer expressão.  
  
 `expression2`  
 Qualquer expressão.  
  
## <a name="remarks"></a>Comentários  
 Se `expression1` for avaliado como `false`, `result` é `expression1`. Caso contrário, `result` é `expression2`. Consequentemente, a operação retorna `true` se ambos os operandos forem verdadeiros; caso contrário, retornará `false`.  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] usa as seguintes regras para converter valores não boolianos para valores booleanos:  
  
-   Todos os objetos são considerados `true`.  
  
-   As cadeias de caracteres são consideradas `false` se elas estiverem vazias.  
  
-   `null` e `undefined` são considerados `false`.  
  
-   Um número é `false` se for zero.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)