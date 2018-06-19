---
title: Operador de espalhamento (...) (JavaScript) | Microsoft Docs
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
ms.assetid: 10263a4c-bd27-4d87-9917-fb4b6bf373db
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a07d480360441906c445faa196f6d7771f97d75d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640226"
---
# <a name="spread-operator--javascript"></a>Operador de espalhamento (...) (JavaScript)
Permite que partes de um literal de matriz sejam inicializadas por meio de uma expressão que pode ser iterada (como outro literal de matriz) ou permite que uma expressão seja expandida para vários argumentos (em chamadas de função).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
var array = [[arg0ToN ,] ...iterable [, arg0ToN]]  
func([args ,] ...iterable [, args | ...iterable])  
  
```  
  
## <a name="parameters"></a>Parâmetros  
 `iterable`  
 Necessário. Um objeto que pode ser iterado.  
  
 `arg0ToN`  
 Opcional. Um ou mais elementos de um literal de matriz.  
  
 `args`  
 Opcional. Um ou mais argumentos para uma função.  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre iteradores, consulte [iteradores e geradores](../../javascript/advanced/iterators-and-generators-javascript.md). Para obter mais informações sobre como usar o operador de difusão como um parâmetro rest, consulte [funções](../../javascript/functions-javascript.md).  
  
## <a name="example"></a>Exemplo  
 Neste exemplo de código a seguir, o uso do operador de difusão é contrastado com o uso do método `concat`.  
  
```JavaScript  
var a, b, c, d, e;  
a = [1,2,3];  
b = "dog";  
c = [42, "cat"];  
  
// Using the concat method.  
d = a.concat(b, c);  
  
// Using the spread operator.  
e = [...a, b, ...c];  
  
console.log(d);  
console.log(e);  
  
// Output:  
// 1, 2, 3, "dog", 42, "cat"  
// 1, 2, 3, "dog", 42, "cat"  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como usar o operador de difusão em uma chamada de função. Neste exemplo, dois literais de matriz são passados para a função usando o operador de difusão e as matrizes são expandidas para vários argumentos.  
  
```JavaScript  
function f(a, b, c, x, y, z) {  
  return a + b + c + x + y + z;  
}  
  
var args = [1, 2, 3];  
console.log(f(...args, 4, ...[5, 6]));  
  
// Output:  
// 21  
  
```  
  
## <a name="example"></a>Exemplo  
 Com os operadores de difusão, você pode simplificar o código que antes exigia o uso de `apply`.  
  
```JavaScript  
function f(x, y, z) {  
    return x + y + z;  
}  
  
var args = [1, 2, 3];  
  
// Old method  
f.apply(this, args);  
// New method  
f(...args);  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)