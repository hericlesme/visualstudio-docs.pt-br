---
title: Método every (Array) (JavaScript) | Microsoft Docs
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
- every method
- arrays [JavaScript], every method
ms.assetid: dc4ee2f8-fb9e-4c9f-af5a-fe836e40ddd1
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a05263ae45df61c47a3580d474863c8d4ff3dd1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637396"
---
# <a name="every-method-array-javascript"></a>Método every (Array) (JavaScript)
Determina se todos os membros de uma matriz satisfazem o teste especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
array1.every(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Definição|  
|---------------|----------------|  
|`array1`|Necessário. Um objeto de matriz.|  
|`callbackfn`|Necessário. Uma função que aceita até três argumentos. O `every` chamadas de método de `callbackfn` função para cada elemento na `array1` até que o `callbackfn` retorna `false`, ou até o fim da matriz.|  
|`thisArg`|Opcional. Um objeto ao qual a palavra-chave `this` pode fazer referência na função `callbackfn`. Se `thisArg` for omitido, `undefined` será usado como o valor de `this`.|  
  
## <a name="return-value"></a>Valor de retorno  
 `true`Se o `callbackfn` função retorna `true` para matriz de todos os elementos; caso contrário, `false`. Se a matriz não tem elementos, o `every` método retornará `true`.  
  
## <a name="exceptions"></a>Exceções  
 Se o argumento `callbackfn` não for um objeto de função, uma exceção `TypeError` será acionada.  
  
## <a name="remarks"></a>Comentários  
 O `every` chamadas de método de `callbackfn` função uma vez para cada elemento da matriz, no índice ordem crescente, até que o `callbackfn` função retorna `false`. Se um elemento que faz com que `callbackfn` para retornar `false` for encontrado, o `every` método retorna imediatamente `false`. Caso contrário, o `every` método retornará `true`.  
  
 A função de retorno de chamada não é chamada para elementos ausentes da matriz.  
  
 Além de objetos de matriz, o método `every` pode ser usado por qualquer objeto que tenha uma propriedade `length` e nomes de propriedade numericamente indexados.  
  
> [!NOTE]
>  Você pode usar o [método some (Array)](../../javascript/reference/some-method-array-javascript.md) para verificar se a função de retorno de chamada retorna `true` para todos os elementos de uma matriz.  
  
## <a name="callback-function-syntax"></a>Sintaxe da função de retorno de chamada  
 A sintaxe da função de retorno de chamada é a seguinte:  
  
 `function callbackfn(value, index, array1)`  
  
 Você pode declarar a função de retorno de chamada com até três parâmetros.  
  
 A tabela a seguir lista os parâmetros da função de retorno de chamada.  
  
|Parâmetro de retorno de chamada|Definição|  
|------------------------|----------------|  
|`value`|O valor do elemento da matriz.|  
|`index`|O índice numérico do elemento da matriz.|  
|`array1`|O objeto de matriz que contém o elemento.|  
  
## <a name="modifying-the-array-object"></a>Modificando o objeto de matriz  
 O objeto de matriz pode ser modificado pela função de retorno de chamada.  
  
 A tabela a seguir descreve os resultados da modificação do objeto de matriz após o início do método `every`.  
  
|Condição após o início do método `every`|Elemento passado para a função de retorno de chamada?|  
|-----------------------------------------------|------------------------------------------|  
|O elemento é adicionado além do comprimento original da matriz.|Nº|  
|O elemento é adicionado para preencher um elemento ausente da matriz.|Sim, se o índice ainda não tiver sido passado para a função de retorno de chamada.|  
|O elemento é alterado.|Sim, se o elemento ainda não tiver sido passado para a função de retorno de chamada.|  
|O elemento é excluído da matriz.|Não, a menos que esse elemento já tenha sido passado para a função de retorno de chamada.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `every`.  
  
```JavaScript  
// Define the callback function.  
function CheckIfEven(value, index, ar) {  
    document.write(value + " ");  
  
    if (value % 2 == 0)  
        return true;  
    else  
        return false;  
}  
  
// Create an array.  
var numbers = [2, 4, 5, 6, 8];  
  
// Check whether the callback function returns true for all of the  
// array values.  
if (numbers.every(CheckIfEven))  
    document.write("All are even.");  
else  
    document.write("Some are not even.");  
  
// Output:  
// 2 4 5 Some are not even.  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do argumento `thisArg` que especifica um objeto ao qual a palavra-chave `this` pode fazer referência.  
  
```JavaScript  
// Create a function that returns true if the value is  
// numeric and within range.  
var checkNumericRange = function(value) {  
    if (typeof value !== 'number')  
        return false;  
    else   
        return value >= this.minimum && value <= this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [10, 15, 19];  
  
// Check whether the callback function returns true for  
// all of the array values.  
// The obj argument enables use of the this value  
// within the callback function.  
  
var obj = { minimum: 10, maximum: 20 }  
  
if (numbers.every(checkNumericRange, obj))  
    document.write ("All are within range.");  
else  
    document.write ("Some are not within range.");  
  
// Output:  
//   All are within range.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método some (Array)](../../javascript/reference/some-method-array-javascript.md)   
 [Método Filter (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [Objeto Array](../../javascript/reference/array-object-javascript.md)   
 [Usando matrizes](../../javascript/advanced/using-arrays-javascript.md)