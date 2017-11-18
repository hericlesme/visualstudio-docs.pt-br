---
title: "Método forEach (Array) (JavaScript) | Microsoft Docs"
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
- forEach method [JavaScript]
- arrays [JavaScript], forEach method
- callback function, forEach method [JavaScript]
ms.assetid: bd188034-a62b-4cbd-99c8-46d70dd6823d
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec35c49e272ba50e26d3e4e7d892aa719a090d73
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="foreach-method-array-javascript"></a>Método forEach (Array) (JavaScript)
Executa a ação especificada para cada elemento de uma matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
array1.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Definição|  
|---------------|----------------|  
|`array1`|Necessário. Um objeto de matriz.|  
|`callbackfn`|Necessário. Uma função que aceita até três argumentos. `forEach` chama a função `callbackfn` uma vez para cada elemento da matriz.|  
|`thisArg`|Opcional. Um objeto ao qual a palavra-chave `this` pode fazer referência na função `callbackfn`. Se `thisArg` for omitido, `undefined` será usado como o valor de `this`.|  
  
## <a name="exceptions"></a>Exceções  
 Se o argumento `callbackfn` não for um objeto de função, uma exceção `TypeError` será acionada.  
  
## <a name="remarks"></a>Comentários  
 O método `forEach` chama a função `callbackfn` uma vez para cada elemento presente na matriz, em ordem de índice crescente. A função de retorno de chamada não é chamada para elementos ausentes da matriz.  
  
 Além de objetos de matriz, o método `forEach` pode ser usado por qualquer objeto que tenha uma propriedade `length` e nomes de propriedade numericamente indexados.  
  
## <a name="callback-function-syntax"></a>Sintaxe da função de retorno de chamada  
 A sintaxe da função de retorno de chamada é a seguinte:  
  
 `function callbackfn(value, index, array1)`  
  
 Você pode declarar a função de retorno de chamada usando até três parâmetros.  
  
 Os parâmetros da função de retorno de chamada são os seguintes.  
  
|Argumento de retorno de chamada|Definição|  
|-----------------------|----------------|  
|`value`|O valor do elemento da matriz.|  
|`index`|O índice numérico do elemento da matriz.|  
|`array1`|O objeto de matriz que contém o elemento.|  
  
## <a name="modifying-the-array-object"></a>Modificando o objeto de matriz  
 O método `forEach` não modifica diretamente a matriz original, mas a função de retorno de chamada pode modificá-la. A tabela a seguir descreve os resultados da modificação do objeto de matriz após o início do método `forEach`.  
  
|Condição após o início do método `forEach`|Elemento passado para a função de retorno de chamada?|  
|---------------------------------------------|------------------------------------------|  
|O elemento é adicionado além do comprimento original da matriz.|Nº|  
|O elemento é adicionado para preencher um elemento ausente da matriz.|Sim, se o índice ainda não tiver sido passado para a função de retorno de chamada.|  
|O elemento é alterado.|Sim, se o elemento ainda não tiver sido passado para a função de retorno de chamada.|  
|O elemento é excluído da matriz.|Não, a menos que esse elemento já tenha sido passado para a função de retorno de chamada.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `forEach`.  
  
```JavaScript  
// Define the callback function.  
function ShowResults(value, index, ar) {  
    document.write("value: " + value);  
    document.write(" index: " + index);  
    document.write("<br />");  
}  
  
// Create an array.  
var letters = ['ab', 'cd', 'ef'];  
  
// Call the ShowResults callback function for each  
// array element.  
letters.forEach(ShowResults);  
  
// Output:  
//  value: ab index: 0   
//  value: cd index: 1   
//  value: ef index: 2   
```  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o argumento `callbackfn` inclui o código da função de retorno de chamada.  
  
```JavaScript  
// Create an array.  
var numbers = [10, 11, 12];  
  
// Call the addNumber callback function for each array element.  
var sum = 0;  
numbers.forEach(  
    function addNumber(value) { sum += value; }  
);  
  
document.write(sum);  
// Output: 33  
  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do argumento `thisArg`, o qual especifica um objeto que pode ser referenciado com a palavra-chave `this`.  
  
```JavaScript  
// Define the object that contains the callback function.  
var obj = {  
    showResults: function(value, index) {  
        // Call calcSquare by using the this value.  
        var squared = this.calcSquare(value);  
  
        document.write("value: " + value);  
        document.write(" index: " + index);  
        document.write(" squared: " + squared);  
        document.write("<br />");  
    },  
    calcSquare: function(x) { return x * x }  
};  
  
// Define an array.  
var numbers = [5, 6];  
  
// Call the showResults callback function for each array element.  
// The obj is the this value within the   
// callback function.  
numbers.forEach(obj.showResults, obj);  
  
// Embed the callback function in the forEach statement.  
// The obj argument is the this value within the obj object.  
// The output is the same as for the previous statement.  
numbers.forEach(function(value, index) { this.showResults(value, index) }, obj);  
  
// Output:  
//  value: 5 index: 0 squared: 25  
//  value: 6 index: 1 squared: 36  
//  value: 5 index: 0 squared: 25  
//  value: 6 index: 1 squared: 36  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método Filter (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [Método Map (Array)](../../javascript/reference/map-method-array-javascript.md)   
 [Método some (Array)](../../javascript/reference/some-method-array-javascript.md)   
 [Objeto Array](../../javascript/reference/array-object-javascript.md)   
 [Usando matrizes](../../javascript/advanced/using-arrays-javascript.md)   
 [Aplicativo de exemplo de JavaScript Hilo (Windows Store)](http://hilojs.codeplex.com/SourceControl/latest)