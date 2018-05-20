---
title: Método reduce (Array) (JavaScript) | Microsoft Docs
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
- callback function, reduce method [JavaScript]
- arrays [JavaScript], reduce method
- reduce method [JavaScript]
ms.assetid: 48d069e0-e083-494f-86d5-d459d2377dc5
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d99f92d90885f26b19392b476ee64ae17bd40aed
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="reduce-method-array-javascript"></a>Método reduce (Array) (JavaScript)
Chama a função de retorno de chamada especificada para todos os elementos em uma matriz. O valor retornado da função de retorno de chamada é o resultado acumulado e é fornecido como um argumento na próxima chamada para a função de retorno de chamada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
array1.reduce(callbackfn[, initialValue])  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Definição|  
|---------------|----------------|  
|`array1`|Necessário. Um objeto de matriz.|  
|`callbackfn`|Necessário. Uma função que aceita até quatro argumentos. O método `reduce` chama a função `callbackfn` uma vez para cada elemento da matriz.|  
|`initialValue`|Opcional. Se `initialValue` for especificado, ele é usado como o valor inicial para iniciar o acúmulo. A primeira chamada para o `callbackfn` função fornece esse valor como um argumento, em vez de um valor de matriz.|  
  
## <a name="return-value"></a>Valor de retorno  
 O resultado acumulado da última chamada para a função de retorno de chamada.  
  
## <a name="exceptions"></a>Exceções  
 Um `TypeError` exceção é lançada quando uma das seguintes condições for verdadeira:  
  
-   O `callbackfn` argumento não é um objeto de função.  
  
-   A matriz não contém elementos e `initialValue` não for fornecido.  
  
## <a name="remarks"></a>Comentários  
 Se um `initialValue` for fornecido, o `reduce` chamadas de método de `callbackfn` função uma vez para cada elemento presente na matriz, no índice de ordem crescente. Se um `initialValue` não for fornecido, o `reduce` chamadas de método de `callbackfn` função em cada elemento, começando com o segundo elemento.  
  
 O valor de retorno da função de retorno de chamada é fornecido como o `accumulator` argumento na próxima chamada para a função de retorno de chamada. O valor de retorno da última chamada para a função de retorno de chamada é o valor de retorno de `reduce` método.  
  
 A função de retorno de chamada não é chamada para elementos ausentes da matriz.  
  
> [!NOTE]
>  O [método reduceRight (Array)](../../javascript/reference/reduceright-method-array-javascript.md) processa os elementos no índice de ordem decrescente.  
  
## <a name="callback-function-syntax"></a>Sintaxe da função de retorno de chamada  
 A sintaxe da função de retorno de chamada é a seguinte:  
  
 `function callbackfn(accumulator, currentValue, currentIndex, array1)`  
  
 Você pode declarar a função de retorno de chamada usando até quatro parâmetros.  
  
 A tabela a seguir lista os parâmetros da função de retorno de chamada.  
  
|Argumento de retorno de chamada|Definição|  
|-----------------------|----------------|  
|`accumulator`|O valor da chamada anterior para a função de retorno de chamada. Se um `initialValue` é fornecido para o `reduce` método, o `accumulator` é `initialValue` na primeira vez em que a função é chamada.|  
|`currentValue`|O valor do elemento da matriz atual.|  
|`currentIndex`|O índice numérico do elemento da matriz atual.|  
|`array1`|O objeto de matriz que contém o elemento.|  
  
## <a name="first-call-to-the-callback-function"></a>Primeira chamada para a função de retorno de chamada  
 Na primeira vez em que a função de retorno de chamada é chamada, os valores fornecidos como argumentos dependem se o `reduce` método tem um `initialValue` argumento.  
  
 Se um `initialValue` é fornecido para o método de redução:  
  
-   O argumento `accumulator` é `initialValue`.  
  
-   O `currentValue` argumento é o valor do primeiro elemento presente na matriz.  
  
 Se um `initialValue` não é fornecida:  
  
-   O `accumulator` argumento é o valor do primeiro elemento presente na matriz.  
  
-   O `currentValue` argumento é o valor do segundo elemento presente na matriz.  
  
## <a name="modifying-the-array-object"></a>Modificando o objeto de matriz  
 O objeto de matriz pode ser modificado pela função de retorno de chamada.  
  
 A tabela a seguir descreve os resultados da modificação do objeto de matriz após o início do método `reduce`.  
  
|Condição após o início do método `reduce`|Elemento passado para a função de retorno de chamada?|  
|------------------------------------------------|------------------------------------------|  
|O elemento é adicionado além do comprimento original da matriz.|Nº|  
|O elemento é adicionado para preencher um elemento ausente da matriz.|Sim, se o índice ainda não tiver sido passado para a função de retorno de chamada.|  
|O elemento é alterado.|Sim, se o elemento ainda não tiver sido passado para a função de retorno de chamada.|  
|O elemento é excluído da matriz.|Não, a menos que esse elemento já tenha sido passado para a função de retorno de chamada.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir concatena os valores de matriz em uma cadeia de caracteres, separando os valores com "::". Como nenhum valor inicial é fornecida para o `reduce` método, a primeira chamada para a função de retorno de chamada tem "abc" como o `accumulator` argumento e "def" como o `currentValue` argumento.  
  
```JavaScript  
// Define the callback function.  
function appendCurrent (accumulator, currentValue) {  
    return accumulator + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduce method, which calls the callback function  
// for each array element.  
var result = elements.reduce(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  abc::def::123::456  
  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir adiciona os valores de uma matriz depois que elas foram arredondadas. O `reduce` método for chamado com um valor inicial de 0.  
  
```JavaScript  
// Define the callback function.  
function addRounded (accumulator, currentValue) {  
    return accumulator + Math.round(currentValue);  
    }  
  
// Create an array.  
var numbers = [10.9, 15.4, 0.5];  
  
// Call the reduce method, starting with an initial value of 0.  
var result = numbers.reduce(addRounded, 0);  
  
document.write (result);  
// Output: 27  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir adiciona os valores em uma matriz. O `currentIndex` e `array1` parâmetros são usados na função de retorno de chamada.  
  
```JavaScript  
function addDigitValue(accumulator, currentDigit, currentIndex, array) {  
    var exponent = (array.length - 1) - currentIndex;  
    var digitValue = currentDigit * Math.pow(10, exponent);  
    return accumulator + digitValue;  
    }  
  
var digits = [4, 1, 2, 5];  
  
// Determine an integer that is computed from values in the array.  
var result = digits.reduce(addDigitValue, 0);  
  
document.write (result);  
// Output: 4125  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir obtém uma matriz que contém apenas os valores que estão entre 1 e 10 na outra matriz. O valor inicial fornecido para o `reduce` método é uma matriz vazia.  
  
```JavaScript  
function Process(accumulatedArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = accumulatedArray.concat(currentValue);  
    else  
        nextArray = accumulatedArray;  
  
    // If this is not the last call by the reduce method,  
    // the returned array is accumulatedArray on the next call.  
    // If this is the last call by the reduce method, the  
    // returned array is the return value of the reduce method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduce method, starting with an initial empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduce(Process, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
// result array=1,6,3  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método reduceRight (Array)](../../javascript/reference/reduceright-method-array-javascript.md)
