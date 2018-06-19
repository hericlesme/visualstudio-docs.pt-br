---
title: Método forEach (Set) (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 813bff6e-6098-4260-ab6e-b0d2da6be94d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b89c56b54fd74c25c43a84f2f0fd68922aa9f637
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636756"
---
# <a name="foreach-method-set-javascript"></a>Método forEach (Set) (JavaScript)
Executa a ação especificada para cada elemento em um conjunto.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
setObj.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `setObj`  
 Necessário. Um objeto `Set`.  
  
 `callbackfn`  
 Necessário. `callbackfn`aceita até três argumentos. A função que `forEach` chama uma vez para cada elemento do conjunto.  
  
 `thisArg`  
 Opcional. Um objeto que o `this` pode referir-se na palavra-chave de `callbackfn` função. Se `thisArg` for omitido, `undefined` será usado como o valor de `this`.  
  
## <a name="exceptions"></a>Exceções  
 Se o argumento `callbackfn` não for um objeto de função, uma exceção `TypeError` será acionada.  
  
## <a name="remarks"></a>Comentários  
 A sintaxe da função de retorno de chamada é a seguinte:  
  
 `function callbackfn(value, key, setObj)`  
  
 Você pode declarar a função de retorno de chamada usando até três parâmetros, conforme mostrado na tabela a seguir.  
  
|Argumento de retorno de chamada|Definição|  
|-----------------------|----------------|  
|`value`|Um valor contido no conjunto.|  
|`key`|Um valor contido no conjunto. Um conjunto não tem chaves, esse valor é o mesmo como `value`.|  
|`setObj`|O `Set` objeto passem.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar `forEach`. O `callbackfn` argumento inclui o código para a função de retorno de chamada.  
  
```JavaScript  
var s = new Set();  
  
s.add("scale");  
s.add(10);  
s.add("5");  
  
s.forEach(function(item, sameItem, s) {  
    document.write("Size of the set object is: " + s.size + "<br />");  
    document.write("Deleting item: " + item + "<br />");  
    s.delete(sameItem);  
});  
  
// Output:  
// Size of the set object is: 3  
// Deleting item: scale  
// Size of the set object is: 2  
// Deleting item: 10  
// Size of the set object is: 1  
// Deleting item: 5  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra que você também pode recuperar membros de um conjunto, passando apenas um único parâmetro para a função de retorno de chamada.  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]