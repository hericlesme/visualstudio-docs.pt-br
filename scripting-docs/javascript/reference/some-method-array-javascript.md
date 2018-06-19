---
title: Método some (Array) (JavaScript) | Microsoft Docs
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
- arrays [JavaScript], some method
- some method [JavaScript]
ms.assetid: 7b6822f9-c406-4f4e-bfec-a93459745992
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba3f855c61daac511bcf7aca6b47f643dda93313
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641756"
---
# <a name="some-method-array-javascript"></a>Método some (Array) (JavaScript)
Determina se a função de retorno de chamada especificada retorna `true` para todos os elementos de uma matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
array1.some(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Definição|  
|---------------|----------------|  
|`array1`|Necessário. Um objeto de matriz.|  
|`callbackfn`|Necessário. Uma função que aceita até três argumentos. O `some` chamadas de método de `callbackfn` função para cada elemento na `array1` até que o `callbackfn` retorna `true`, ou até o fim da matriz.|  
|`thisArg`|Opcional. Um objeto ao qual a palavra-chave `this` pode fazer referência na função `callbackfn`. Se `thisArg` for omitido, `undefined` será usado como o valor de `this`.|  
  
## <a name="return-value"></a>Valor de retorno  
 `true`Se o `callbackfn` função retorna `true` para qualquer elemento da matriz; caso contrário, `false`.  
  
## <a name="exceptions"></a>Exceções  
 Se o argumento `callbackfn` não for um objeto de função, uma exceção `TypeError` será acionada.  
  
## <a name="remarks"></a>Comentários  
 O `some` chamadas de método de `callbackfn` função em cada elemento da matriz, no índice ordem crescente, até que o `callbackfn` função retorna `true`. Se um elemento que faz com que `callbackfn` para retornar `true` for encontrado, o `some` método retorna imediatamente `true`. Se o retorno de chamada não retornar `true` em qualquer elemento, o `some` método retornará `false`.  
  
 A função de retorno de chamada não é chamada para elementos ausentes da matriz.  
  
 Além de objetos de matriz, o método `some` pode ser usado por qualquer objeto que tenha uma propriedade `length` e nomes de propriedade numericamente indexados.  
  
> [!NOTE]
>  Você pode usar o [método every (Array)](../../javascript/reference/every-method-array-javascript.md) para verificar se a função de retorno de chamada retorna `true` para todos os elementos de uma matriz.  
  
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
  
 A tabela a seguir descreve os resultados da modificação do objeto de matriz após o início do método `some`.  
  
|Condição após o início do método `some`|Elemento passado para a função de retorno de chamada?|  
|----------------------------------------------|------------------------------------------|  
|O elemento é adicionado além do comprimento original da matriz.|Nº|  
|O elemento é adicionado para preencher um elemento ausente da matriz.|Sim, se o índice ainda não tiver sido passado para a função de retorno de chamada.|  
|O elemento é alterado.|Sim, se o elemento ainda não tiver sido passado para a função de retorno de chamada.|  
|O elemento é excluído da matriz.|Não, a menos que esse elemento já tenha sido passado para a função de retorno de chamada.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `some` método para verificar se todos os elementos em uma matriz são pares.  
  
```JavaScript  
// The callback function.  
function CheckIfEven(value, index, ar) {  
    if (value % 2 == 0)  
        return true;  
}  
  
var numbers = [1, 15, 4, 10, 11, 22];  
  
var evens = numbers.some(CheckIfEven);  
document.write(evens);  
  
// Output:  
// true  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `thisArg` parâmetro, que especifica um objeto ao qual o `this` pode se referir a palavra-chave. Ele verifica se qualquer um dos números em uma matriz está fora do intervalo fornecido por um objeto passado  
  
```JavaScript  
// Create a function that returns true if the value is   
// outside the range.  
var isOutsideRange = function (value) {  
    return value < this.minimum || value > this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [6, 12, 16, 22, -12];  
  
// The range object is to be the 'this' object.  
var range = { minimum: 10, maximum: 20 };  
  
document.write(numbers.some(isOutsideRange, range));  
  
// Output: true  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método every (Array)](../../javascript/reference/every-method-array-javascript.md)   
 [Método Filter (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [Método map (Array)](../../javascript/reference/map-method-array-javascript.md)