---
title: Método lastIndexOf (matriz) (JavaScript) | Microsoft Docs
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
- arrays [JavaScript], lastIndexOf method
- lastIndexOf method [JavaScript]
ms.assetid: 04f5145d-007e-498f-b06f-11ab384c2968
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12d2a0fca7a7cd82543a83ea19aca49d3cbb93b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638056"
---
# <a name="lastindexof-method-array-javascript"></a>Método lastIndexOf (Array) (JavaScript)
Retorna o índice da última ocorrência de um valor especificado em uma matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
array1.lastIndexOf(searchElement[, fromIndex])  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Definição|  
|---------------|----------------|  
|`array1`|Necessário. O objeto de matriz para pesquisar.|  
|`searchElement`|Necessário. O valor a ser localizado na `array1`.|  
|`fromIndex`|Opcional. O índice de matriz no qual iniciar a pesquisa. Se `fromIndex` for omitido, a pesquisa começa no último índice na matriz.|  
  
## <a name="return-value"></a>Valor de retorno  
 O índice da última ocorrência de `searchElement` na matriz, ou -1 se `searchElement` não foi encontrado.  
  
## <a name="remarks"></a>Comentários  
 O `lastIndexOf` método procura uma matriz para um valor especificado. O método retorna o índice da primeira ocorrência ou -1 se o valor especificado não foi encontrado.  
  
 A pesquisa ocorre no índice de ordem decrescente (do último membro primeiro). Para pesquisar em ordem crescente, use o [método indexOf (matriz)](../../javascript/reference/indexof-method-array-javascript.md).  
  
 Os elementos da matriz são comparados com o `searchElement` valor por Igualdade estrita, semelhante à comparação feita pelo `===` operador. Para obter mais informações, consulte [operadores de comparação](../../javascript/reference/comparison-operators-javascript.md).  
  
 Opcional `fromIndex` argumento especifica o índice de matriz no qual iniciar a pesquisa. Se `fromIndex` for maior que ou igual ao comprimento da matriz, a matriz inteira será pesquisada. Se `fromIndex` é negativo, a pesquisa começa no comprimento da matriz mais `fromIndex`. Se o índice calculado é menor que 0, -1 será retornado.  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir ilustram o uso do `lastIndexOf` método.  
  
```JavaScript  
// Create an array.  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location, in descending order, of "cd".  
document.write(ar.lastIndexOf("cd") + "<br/>");  
  
// Output: 4  
  
// Find "cd" in descending order, starting at index 2.  
document.write(ar.lastIndexOf("cd", 2) + "<br/>");  
  
// Output: 1  
  
// Search for "gh" (which is not found).  
document.write(ar.lastIndexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -3.  
// The search in descending order starts at index 3,  
// which is the array length minus 2.  
document.write(ar.lastIndexOf("ab", -3) + "<br/>");  
// Output: 0  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método indexOf (matriz)](../../javascript/reference/indexof-method-array-javascript.md)   
 [Objeto Array](../../javascript/reference/array-object-javascript.md)   
 [Usando matrizes](../../javascript/advanced/using-arrays-javascript.md)