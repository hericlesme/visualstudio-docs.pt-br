---
title: "Método Filter (Array) (JavaScript) | Microsoft Docs"
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
- arrays [JavaScript], filter method
- filter method [JavaScript]
ms.assetid: 1d260370-9e6e-43fc-870f-2d35850db7ee
caps.latest.revision: "32"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33a08fdba38de558dabc749a634fb9b69c52c98a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="filter-method-array-javascript"></a>Método filter (Array) (JavaScript)
Retorna os elementos de uma matriz que atendem à condição especificada em uma função de retorno de chamada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
array1.filter(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Definição|  
|---------------|----------------|  
|`array1`|Necessário. Um objeto de matriz.|  
|`callbackfn`|Necessário. Uma função que aceita até três argumentos. O método `filter` chama a função `callbackfn` uma vez para cada elemento da matriz.|  
|`thisArg`|Opcional. Um objeto ao qual a palavra-chave `this` pode fazer referência na função `callbackfn`. Se `thisArg` for omitido, `undefined` será usado como o valor de `this`.|  
  
## <a name="return-value"></a>Valor de retorno  
 Uma nova matriz que contém todos os valores para os quais a função de retorno de chamada retorna `true`. Se a função de retorno de chamada retorna `false` para todos os elementos de `array1`, o comprimento da nova matriz é 0.  
  
## <a name="exceptions"></a>Exceções  
 Se o argumento `callbackfn` não for um objeto de função, uma exceção `TypeError` será acionada.  
  
## <a name="remarks"></a>Comentários  
 O método `filter` chama a função `callbackfn` uma vez para cada elemento existente na matriz, em ordem de índice crescente. A função de retorno de chamada não é chamada para elementos ausentes da matriz.  
  
 Além de objetos de matriz, o método `filter` pode ser usado por qualquer objeto que tenha uma propriedade `length` e nomes de propriedade numericamente indexados.  
  
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
 O método `filter` não modifica diretamente a matriz original, mas a função de retorno de chamada pode modificá-la. A tabela a seguir descreve os resultados da modificação do objeto de matriz após o início do método `filter`.  
  
|Condição após o início do método `filter`|Elemento passado para a função de retorno de chamada?|  
|------------------------------------------------|------------------------------------------|  
|O elemento é adicionado além do comprimento original da matriz.|Nº|  
|O elemento é adicionado para preencher um elemento ausente da matriz.|Sim, se o índice ainda não tiver sido passado para a função de retorno de chamada.|  
|O elemento é alterado.|Sim, se o elemento ainda não tiver sido passado para a função de retorno de chamada.|  
|O elemento é excluído da matriz.|Não, a menos que esse elemento já tenha sido passado para a função de retorno de chamada.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o método `filter`.  
  
```JavaScript  
// Define a callback function.  
function CheckIfPrime(value, index, ar) {  
    high = Math.floor(Math.sqrt(value)) + 1;  
  
    for (var div = 2; div <= high; div++) {  
        if (value % div == 0) {  
            return false;  
        }  
    }   
    return true;  
}  
  
// Create the original array.  
var numbers = [31, 33, 35, 37, 39, 41, 43, 45, 47, 49, 51, 53];  
  
// Get the prime numbers that are in the original array.   
var primes = numbers.filter(CheckIfPrime);  
  
document.write(primes);  
// Output: 31,37,41,43,47,53  
```  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o argumento `callbackfn` inclui o código da função de retorno de chamada.  
  
```JavaScript  
// Create the original array.  
var arr = [5, "element", 10, "the", true];  
  
// Create an array that contains the string  
// values that are in the original array.  
var result = arr.filter(  
    function (value) {  
        return (typeof value === 'string');  
    }  
);  
  
document.write(result);  
// Output: element, the  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir exibe os nomes das propriedades que começam com a letra "css" o `window` objeto DOM.  
  
```JavaScript  
var filteredNames = Object.getOwnPropertyNames(window).filter(IsC);  
  
    for (i in filteredNames)  
        document.write(filteredNames[i] + "<br/>");  
  
// Check whether the string starts with "css".  
function IsC(value) {  
    var firstChar = value.substr(0, 3);  
    if (firstChar.toLowerCase() == "css")  
        return true;  
    else  
        return false;  
    }  
  
// Output:  
// CSSRule  
// CSSFontFaceRule  
// CSSImportRule  
// CSSMediaRule  
// CSSNamespaceRule  
// CSSPageRule  
// CSSRuleList  
// CSSStyleDeclaration  
// CSSStyleRule  
// CSSStyleSheet  
  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do argumento `thisArg` que especifica um objeto ao qual a palavra-chave `this` pode fazer referência.  
  
```JavaScript  
var checkNumericRange = function(value) {  
    if (typeof value !== 'number')  
        return false;  
    else   
        return value >= this.minimum && value <= this.maximum;  
}  
  
var numbers = [6, 12, "15", 16, "the", -12];  
  
// The obj argument enables use of the this value  
// within the callback function.  
var obj = { minimum: 10, maximum: 20 }  
  
var result = numbers.filter(checkNumericRange, obj);  
  
document.write(result);  
// Output: 12,16  
  
```  
  
## <a name="example"></a>Exemplo  
 O `filter` método pode ser aplicado a uma cadeia de caracteres em vez de uma matriz. O exemplo a seguir mostra como fazer isso.  
  
```JavaScript  
// Define a callback function that returns true  
// if the current array element follows a space  
// or is the first character.  
function CheckValue(value, index, ar) {  
    if (index == 0)  
        return true;  
    else  
        return ar[index - 1] === " ";  
}  
  
// Create a string.  
var sentence = "The quick brown fox jumps over the lazy dog.";   
  
// Create an array that contains all characters that follow a space.  
var subset = [].filter.call(sentence, CheckValue);   
  
// You can use this alternative syntax.  
//var subset = Array.prototype.filter.call(sentence, CheckValue);  
  
document.write(subset);  
// Output: T,q,b,f,j,o,t,l,d  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Array](../../javascript/reference/array-object-javascript.md)   
 [Usando matrizes](../../javascript/advanced/using-arrays-javascript.md)   
 [Método Map (Array)](../../javascript/reference/map-method-array-javascript.md)   
 [Método forEach (Array)](../../javascript/reference/foreach-method-array-javascript.md)