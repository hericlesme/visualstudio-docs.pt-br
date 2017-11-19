---
title: "loop for... de instrução (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7872b0b2-5701-4d72-9b52-ed13991542cc
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47154261fd4817ba95b8884bd6482a87e044a5a4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="forof-statement-javascript"></a>Instrução for...of (JavaScript)
Executa uma ou mais instruções para cada valor de um iterador obtido de um objeto que pode ser iterado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
for (variable of object) {  
    statements   
}  
```  
  
## <a name="parameters"></a>Parâmetros  
 `variable`  
 Necessário. Uma variável que pode ser qualquer valor da propriedade de `object`.  
  
 `object`  
 Necessário. Um objeto que pode ser iterado, como um `Array`, `Map`, `Set`, ou um objeto que implementa o [interfaces de iterador](http://msdn.microsoft.com/en-us/3692355a-a703-4d43-8fb5-c03b4b7e8db1).  
  
 `statements`  
 Opcional. Uma ou mais instruções a serem executadas para cada valor de um `object`. Pode ser uma instrução composta.  
  
## <a name="remarks"></a>Comentários  
 No início de cada iteração de um loop, o valor de `variable` é o próximo valor da propriedade de `object`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da instrução `for...of` em uma função.  
  
```JavaScript  
let arr = [ "fred", "tom", "bob" ];  
  
for (let i of arr) {  
    console.log(i);  
}  
  
// Output:  
// fred  
// tom  
// bob  
  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da instrução `for...of` em um objeto `Map`.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
  
for (var n of m) {  
  console.log(n);  
}  
  
// Output:  
// 1,black  
// 2,red  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [loop for... na instrução](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Instrução for](../../javascript/reference/for-statement-javascript.md)   
 [Instrução while](../../javascript/reference/while-statement-javascript.md)