---
title: loop for... na instrução (JavaScript) | Microsoft Docs
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
helpviewer_keywords:
- iteration statements, for...in statement
- loop structures, for...in statements
ms.assetid: 1b51a0ce-89f7-4a69-88ed-017b47dc398f
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9c3ce78def6ab91256ff724a4acc87b7cf19ba2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636726"
---
# <a name="forin-statement-javascript"></a>Instrução for...in (JavaScript)
Executa uma ou mais instruções para cada propriedade de um objeto ou cada elemento da matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
for (variable in [object | array]) {  
    statements   
}  
```  
  
## <a name="parameters"></a>Parâmetros  
 `variable`  
 Necessário. Uma variável que pode ser qualquer nome de propriedade de `object` ou qualquer índice de elemento de um `array`.  
  
 `object`, `array`  
 Opcional. Um objeto ou uma matriz na qual iterar.  
  
 `statements`  
 Opcional. Um ou mais instruções a serem executadas para cada propriedade de `object` ou cada elemento de `array`. Pode ser uma instrução composta.  
  
## <a name="remarks"></a>Comentários  
 No início de cada iteração de um loop, o valor de `variable` é o nome da propriedade próximo `object` ou o índice do elemento próximo do `array`. Você pode usar `variable` em qualquer uma das instruções dentro do loop para referenciar a propriedade de `object` ou o elemento de `array`.  
  
 As propriedades de um objeto não são atribuídas de forma determinada. Você não pode especificar uma determinada propriedade por seu índice, apenas pelo nome da propriedade.  
  
 Iterando por meio de uma matriz é executada em ordem de elemento, ou seja, 0, 1, 2.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do `for...in` instrução com um objeto usado como uma matriz associativa.  
  
```JavaScript  
// Initialize object.  
a = {"a" : "Athens" , "b" : "Belgrade", "c" : "Cairo"}  
  
// Iterate over the properties.  
var s = ""  
for (var key in a) {  
    s += key + ": " + a[key];  
    s += "<br />";  
    }  
document.write (s);  
  
// Output:  
// a: Athens  
// b: Belgrade  
// c: Cairo  
```  
  
## <a name="example"></a>Exemplo  
 Este exemplo ilustra o uso do `for ... in` instrução para iterar Embora um `Array` objeto que tem propriedades expando.  
  
```JavaScript  
// Initialize the array.  
var arr = new Array("zero","one","two");  
  
// Add a few expando properties to the array.  
arr["orange"] = "fruit";  
arr["carrot"] = "vegetable";  
  
// Iterate over the properties and elements.  
var s = "";  
for (var key in arr) {  
    s += key + ": " + arr[key];  
    s += "<br />";  
}  
  
document.write (s);  
  
// Output:  
//   0: zero  
//   1: one  
//   2: two  
//   orange: fruit  
//   carrot: vegetable  
```  
  
> [!NOTE]
>  Use o `Enumerator` objeto para iterar sobre os membros de uma coleção.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução for](../../javascript/reference/for-statement-javascript.md)   
 [Instrução while](../../javascript/reference/while-statement-javascript.md)