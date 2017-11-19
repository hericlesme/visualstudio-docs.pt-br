---
title: "If... instrução else (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- else_JavaScriptKeyword
- if_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- if statement, if...else
- loop structures, if...else statements
ms.assetid: dfbe86e8-9c1e-4ef5-bb9c-7d1db7ce2506
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fad12b970f69a15040acb59195f957a2a6eec3e0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="ifelse-statement-javascript"></a>Instrução if...else (JavaScript)
Execute um grupo de instruções condicionalmente, dependendo do valor de uma expressão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
if (condition1) {  
    statement1  
}  
[else if (condition2) {  
    statement2  
}]  
[else {  
    statement3]   
}]  
```  
  
## <a name="parameters"></a>Parâmetros  
 `condition1`  
 Necessário. Uma expressão booleana. Se `condition1` é `null` ou `undefined`, `condition1` é tratado como `false`.  
  
 `statement1`  
 Opcional. A instrução a ser executada se `condition1` é **true**. Pode ser uma instrução composta.  
  
 `condition2`  
 A condição a ser avaliada.  
  
 `statement2`  
 Opcional. A instrução a ser executada se `condition2` é `true`. Pode ser uma instrução composta.  
  
 `statement3`  
 Se ambos os `condition1` e `condition2` são `false`, essa instrução é executada.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como usar `if`, `if else`, e `else`.  
  
 É recomendável colocar `statement1` e `statement2` entre chaves ({}) para maior clareza e evitar erros inadvertidamente.  
  
```JavaScript  
var z = 3;  
if (x == 5) {  
    z = 10;  
}  
else if (x == 10) {  
    z = 15;  
}  
else {  
    z = 20;  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador condicional (ternário) (?:)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)