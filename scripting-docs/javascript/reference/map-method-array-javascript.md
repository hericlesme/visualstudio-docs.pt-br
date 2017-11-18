---
title: "Método Map (Array) (JavaScript) | Microsoft Docs"
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
helpviewer_keywords:
- map method [JavaScript]
- arrays [JavaScript], map method
ms.assetid: 500dc4f8-d73d-4a28-a5b8-c9bd5674ea36
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 609d9c88000a7a30fe8edc03b52df032f7d19ba9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="map-method-array-javascript"></a>Método map (Array) (JavaScript)
Chama uma função de retorno de chamada definida em cada elemento de uma matriz e retorna uma matriz que contém os resultados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
array1.map(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Definição|  
|---------------|----------------|  
|`array1`|Necessário. Um objeto de matriz.|  
|`callbackfn`|Necessário. Uma função que aceita até três argumentos. O método `map` chama a função `callbackfn` uma vez para cada elemento da matriz.|  
|`thisArg`|Opcional. Um objeto ao qual a palavra-chave `this` pode fazer referência na função `callbackfn`. Se `thisArg` for omitido, `undefined` será usado como o valor de `this`.|  
  
## <a name="return-value"></a>Valor de retorno  
 Uma nova matriz em que cada elemento é o valor de retorno da função de retorno de chamada para o elemento de matriz original associado.  
  
## <a name="exceptions"></a>Exceções  
 Se o argumento `callbackfn` não for um objeto de função, uma exceção `TypeError` será acionada.  
  
## <a name="remarks"></a>Comentários  
 O método `map` chama a função `callbackfn` uma vez para cada elemento existente na matriz, em ordem de índice crescente. A função de retorno de chamada não é chamada para elementos ausentes da matriz.  
  
 Além de objetos de matriz, o método `map` pode ser usado por qualquer objeto que tenha uma propriedade `length` e nomes de propriedade numericamente indexados.  
  
## <a name="callback-function-syntax"></a>Sintaxe da função de retorno de chamada  
 A sintaxe da função de retorno de chamada é a seguinte:  
  
 `function callbackfn(value, index, array1)`  
  
 Você pode declarar a função de retorno de chamada usando até três parâmetros.  
  
 A tabela a seguir lista os parâmetros da função de retorno de chamada.  
  
|Argumento de retorno de chamada|Definição|  
|-----------------------|----------------|  
|`value`|O valor do elemento da matriz.|  
|`index`|O índice numérico do elemento da matriz.|  
|`array1`|O objeto de matriz que contém o elemento.|  
  
## <a name="modifying-the-array-object"></a>Modificando o objeto de matriz  
 O objeto de matriz pode ser modificado pela função de retorno de chamada.  
  
 A tabela a seguir descreve os resultados da modificação do objeto de matriz após o início do método `map`.  
  
|Condição após o início do método `map`|Elemento passado para a função de retorno de chamada?|  
|---------------------------------------------|------------------------------------------|  
|O elemento é adicionado além do comprimento original da matriz.|Nº|  
|O elemento é adicionado para preencher um elemento ausente da matriz.|Sim, se o índice ainda não tiver sido passado para a função de retorno de chamada.|  
|O elemento é alterado.|Sim, se o elemento ainda não tiver sido passado para a função de retorno de chamada.|  
|O elemento é excluído da matriz.|Não, a menos que esse elemento já tenha sido passado para a função de retorno de chamada.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `map`.  
  
```JavaScript  
// Define the callback function.  
function AreaOfCircle(radius) {  
    var area = Math.PI * (radius * radius);  
    return area.toFixed(0);  
}  
  
// Create an array.  
var radii = [10, 20, 30];  
  
// Get the areas from the radii.  
var areas = radii.map(AreaOfCircle);  
  
document.write(areas);  
  
// Output:  
// 314,1257,2827  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do argumento `thisArg` que especifica um objeto ao qual a palavra-chave `this` pode fazer referência.  
  
```JavaScript  
// Define an object that contains a divisor property and  
// a remainder function.  
var obj = {  
    divisor: 10,  
    remainder: function (value) {  
        return value % this.divisor;  
    }  
}  
  
// Create an array.  
var numbers = [6, 12, 25, 30];  
  
// Get the remainders.  
// The obj argument specifies the this value in the callback function.  
var result = numbers.map(obj.remainder, obj);  
document.write(result);  
  
// Output:  
// 6,2,5,0  
```  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, um método [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] interno é usado como a função de retorno de chamada.  
  
```JavaScript  
// Apply Math.sqrt(value) to each element in an array.  
var numbers = [9, 16];  
var result = numbers.map(Math.sqrt);  
  
document.write(result);  
// Output: 3,4  
```  
  
## <a name="example"></a>Exemplo  
 O método `map` pode ser aplicado a uma cadeia de caracteres. O exemplo a seguir ilustra essa situação.  
  
```JavaScript  
// Define the callback function.  
function threeChars(value, index, str) {  
    // Create a string that contains the previous, current,  
    // and next character.  
    return str.substring(index - 1, index + 2);  
}  
  
// Create a string.  
var word = "Thursday";  
  
// Apply the map method to the string.  
// Each array element in the result contains a string that  
// has the previous, current, and next character.  
// The commented out statement shows an alternative syntax.  
var result = [].map.call(word, threeChars);  
// var result = Array.prototype.map.call(word, threeChars);  
  
document.write(result);  
  
// Output:  
// Th,Thu,hur,urs,rsd,sda,day,ay  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Métodos (JavaScript)](../../javascript/reference/javascript-methods.md)   
 [Objeto Array](../../javascript/reference/array-object-javascript.md)   
 [Usando matrizes](../../javascript/advanced/using-arrays-javascript.md)   
 [Método Filter (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [Método forEach (Array)](../../javascript/reference/foreach-method-array-javascript.md)   
 [Aplicativo de exemplo de JavaScript Hilo (Windows Store)](http://hilojs.codeplex.com/SourceControl/latest)