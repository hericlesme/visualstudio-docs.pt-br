---
title: Método reduceRight (Array) (JavaScript) | Microsoft Docs
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
- arrays [JavaScript], reduceRight method
- reduceRight method [JavaScript]
ms.assetid: 85963761-da11-407c-8bce-278c930e61bd
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d7fd2794157eadacefa7404f9333c51aed9425c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641916"
---
# <a name="reduceright-method-array-javascript"></a>Método reduceRight (Array) (JavaScript)
Chama a função de retorno de chamada especificada para todos os elementos de uma matriz, em ordem decrescente. O valor retornado da função de retorno de chamada é o resultado acumulado e é fornecido como um argumento na próxima chamada para a função de retorno de chamada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
array1.reduceRight(callbackfn[, initialValue])  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Definição|  
|---------------|----------------|  
|`array1`|Necessário. Um objeto de matriz.|  
|`callbackfn`|Necessário. Uma função que aceita até quatro argumentos. O método `reduceRight` chama a função `callbackfn` uma vez para cada elemento da matriz.|  
|`initialValue`|Opcional. Se `initialValue` for especificado, ele é usado como o valor inicial para iniciar o acúmulo. A primeira chamada para o `callbackfn` função fornece esse valor como um argumento, em vez de um valor de matriz.|  
  
## <a name="return-value"></a>Valor de retorno  
 Um objeto que contém o resultado acumulado da última chamada para a função de retorno de chamada.  
  
## <a name="exceptions"></a>Exceções  
 Um `TypeError` exceção é lançada quando uma das seguintes condições for verdadeira:  
  
-   O `callbackfn` argumento não é um objeto de função.  
  
-   A matriz não contém elementos e `initialValue` não for fornecido.  
  
## <a name="remarks"></a>Comentários  
 Se um `initialValue` for fornecido, o `reduceRight` chamadas de método de `callbackfn` função uma vez para cada elemento da matriz, em ordem de índice decrescente. Se nenhum `initialValue` for fornecido, o `reduceRight` chamadas de método de `callbackfn` função em cada elemento, começando com o elemento de segundo ao último, no índice de ordem decrescente.  
  
 O valor de retorno da função de retorno de chamada é fornecido como o `previousValue` argumento na próxima chamada para a função de retorno de chamada. O valor de retorno da última chamada para a função de retorno de chamada é o valor de retorno de `reduceRight` método.  
  
 A função de retorno de chamada não é chamada para elementos ausentes da matriz.  
  
 Para acumular um resultado no índice de ordem crescente, use o [método reduce (Array)](../../javascript/reference/reduce-method-array-javascript.md).  
  
## <a name="callback-function-syntax"></a>Sintaxe da função de retorno de chamada  
 A sintaxe da função de retorno de chamada é a seguinte:  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 Você pode declarar a função de retorno de chamada usando até quatro parâmetros.  
  
 A tabela a seguir lista os parâmetros da função de retorno de chamada.  
  
|Argumento de retorno de chamada|Definição|  
|-----------------------|----------------|  
|`previousValue`|O valor da chamada anterior para a função de retorno de chamada. Se um `initialValue` é fornecido para o `reduceRight` método, o `previousValue` é `initialValue` na primeira vez em que a função é chamada.|  
|`currentValue`|O valor do elemento da matriz atual.|  
|`currentIndex`|O índice numérico do elemento da matriz atual.|  
|`array1`|O objeto de matriz que contém o elemento.|  
  
## <a name="first-call-to-the-callback-function"></a>Primeira chamada para a função de retorno de chamada  
 Na primeira vez em que a função de retorno de chamada é chamada, os valores fornecidos como argumentos dependem se o `reduceRight` método tem um `initialValue` argumento.  
  
 Se um `initialValue` é fornecido para o `reduceRight` método:  
  
-   O argumento `previousValue` é `initialValue`.  
  
-   O `currentValue` argumento é o valor do último elemento presente na matriz.  
  
 Se um `initialValue` não é fornecida:  
  
-   O `previousValue` argumento é o valor do último elemento presente na matriz.  
  
-   O `currentValue` argumento é o valor do segundo ao último elemento presente na matriz.  
  
## <a name="modifying-the-array-object"></a>Modificando o objeto de matriz  
 O objeto de matriz pode ser modificado pela função de retorno de chamada.  
  
 A tabela a seguir descreve os resultados da modificação do objeto de matriz após o início do método `reduceRight`.  
  
|Condição após o início do método `reduceRight`|Elemento passado para a função de retorno de chamada?|  
|-----------------------------------------------------|------------------------------------------|  
|O elemento é adicionado além do comprimento original da matriz.|Nº|  
|O elemento é adicionado para preencher um elemento ausente da matriz.|Sim, se o índice ainda não tiver sido passado para a função de retorno de chamada.|  
|O elemento é alterado.|Sim, se o elemento ainda não tiver sido passado para a função de retorno de chamada.|  
|O elemento é excluído da matriz.|Não, a menos que esse elemento já tenha sido passado para a função de retorno de chamada.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir concatena os valores de matriz em uma cadeia de caracteres, separando os valores com "::". Como nenhum valor inicial é fornecida para o `reduceRight` método, a primeira chamada para a função de retorno de chamada tem 456 como o `previousValue` argumento e 123 como o `currentValue` argumento.  
  
```JavaScript  
// Define the callback function.  
function appendCurrent (previousValue, currentValue) {  
    return previousValue + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduceRight method, which calls the callback function  
// for each array element, in descending index order.  
var result = elements.reduceRight(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  456::123::def::abc  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir localiza a soma dos quadrados dos elementos da matriz. O `reduceRight` método for chamado com um valor inicial de 0.  
  
```JavaScript  
// Define the callback function.  
function Process(previousValue, currentValue, index, array) {  
    // Add the previous value to the current value squared.  
    var nextValue = previousValue + (currentValue * currentValue);  
  
    // If this is not the last call by the reduceRight method,  
    // the return value is previousValue on the next call.  
    // If this is the last call by the reduceRight method, the  
    // return value is the return value of the reduceRight method.  
    return nextValue;  
}  
  
// Create an array.  
var numbers = [3, 4, 5];  
  
// Call the reduceRight method with an initial value of 0.  
var sumOfSquares = numbers.reduceRight(Process, 0);  
  
document.write("sum of squares=" + sumOfSquares);  
  
// Output:  
//  sum of squares=50  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir obtém os elementos de uma matriz cujos valores estejam entre 1 e 10. O valor inicial fornecido para o `reduceRight` método é uma matriz vazia.  
  
```JavaScript  
function Process2(previousArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = previousArray.concat(currentValue);  
    else  
        nextArray = previousArray;  
  
    // If this is not the last call by the reduceRight method,  
    // the returned array is previousArray on the next call.  
    // If this is the last call by the reduceRight method, the  
    // returned array is the return value of the reduceRight method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduceRight method, starting with an empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduceRight(Process2, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
//  result array=3,6,1  
```  
  
## <a name="example"></a>Exemplo  
 O método `reduceRight` pode ser aplicado a uma cadeia de caracteres. O exemplo a seguir mostra como usar esse método para reverter os caracteres em uma cadeia de caracteres.  
  
```JavaScript  
// Define the callback function.  
function AppendToArray(previousValue, currentValue) {  
    return previousValue + currentValue;  
}  
  
var word = "retupmoc";  
  
// Create a string that reverses the characters of another string.  
// The commented-out statement shows an alternative syntax.  
var result = [].reduceRight.call(word, AppendToArray, "the ");  
// var result = Array.prototype.reduceRight.call(word, AppendToArray, "the ");  
  
document.write(result);  
  
// Output:  
// the computer  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método reduce (Array)](../../javascript/reference/reduce-method-array-javascript.md)