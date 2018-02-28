---
title: "Instrução Return (JavaScript) | Microsoft Docs"
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
- return_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- terminating execution
- return statement
- function statement
- return statement, syntax
- return statement, exiting functions in script
ms.assetid: a9130d90-11fb-43f5-a819-7e5435f74c05
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c28f17bed2dfff021ea1aea268bb7a2eb3f3e58
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="return-statement-javascript"></a>Instrução return (JavaScript)
Sai da função atual e retorna um valor daquela função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
return[(][expression][)];   
```  
  
## <a name="remarks"></a>Comentários  
 Opcional *expressão* argumento é o valor a ser retornado da função. Se omitido, a função não retorna um valor.  
  
 Você usa o `return` instrução para parar a execução de uma função e retornar o valor de *expressão*. Se *expressão* for omitido, ou nenhuma `return` instrução é executada de dentro da função, a expressão que chamou a função atual é atribuída o valor indefinido.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da instrução `return`.  
  
```JavaScript  
function myfunction(arg1, arg2){  
   var r;  
   r = arg1 * arg2;  
   return(r);  
}  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do `return` instrução para retornar a uma função.  
  
```JavaScript  
function doWork() {  
    return function calculate(y) { return y + 1; };  
}  
  
var func = doWork();  
var x = func(5);  
document.write(x);  
  
// Output: 6  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Function](../../javascript/reference/function-statement-javascript.md)