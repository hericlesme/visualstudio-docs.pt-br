---
title: Método indexOf (matriz) (JavaScript) | Microsoft Docs
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
- arrays [JavaScript], indexOf method
- indexOf method [JavaScript]
ms.assetid: 5bee31ae-aaf1-4466-8cfd-ed287e3cdf17
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63685219faf42991da6b798493c58b356ab97279
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637476"
---
# <a name="indexof-method-array-javascript"></a>Método indexOf (Array) (JavaScript)
Retorna o índice da primeira ocorrência de um valor em uma matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
array1.indexOf(searchElement[, fromIndex])  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Definição|  
|---------------|----------------|  
|`array1`|Necessário. Um objeto de matriz.|  
|`searchElement`|Necessário. O valor a ser localizado na `array1`.|  
|`fromIndex`|Opcional. O índice de matriz no qual iniciar a pesquisa. Se `fromIndex` for omitido, a pesquisa começa no índice 0.|  
  
## <a name="return-value"></a>Valor de retorno  
 O índice da primeira ocorrência de `searchElement` na matriz, ou -1 se `searchElement` não foi encontrado.  
  
## <a name="remarks"></a>Comentários  
 O `indexOf` método procura uma matriz para um valor especificado. O método retorna o índice da primeira ocorrência ou -1 se o valor especificado não foi encontrado.  
  
 A pesquisa ocorre no índice de ordem crescente.  
  
 Os elementos da matriz são comparados com o `searchElement` valor por Igualdade estrita, semelhante do `===` operador. Para obter mais informações, consulte [operadores de comparação](../../javascript/reference/comparison-operators-javascript.md).  
  
 Opcional `fromIndex` argumento especifica o índice de matriz no qual iniciar a pesquisa. Se `fromIndex` for maior que ou igual ao comprimento da matriz, -1 será retornado. Se `fromIndex` é negativo, a pesquisa começa no comprimento da matriz mais `fromIndex`.  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir ilustram o uso do `indexOf` método.  
  
```JavaScript  
// Create an array. (The elements start at index 0.)  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location of "cd".  
document.write(ar.indexOf("cd") + "<br/>");  
  
// Output: 1  
  
// Find "cd" starting at index 2.  
document.write(ar.indexOf("cd", 2) + "<br/>");  
  
// Output: 4  
  
// Find "gh" (which is not found).  
document.write (ar.indexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -2.  
// The search starts at index 3, which is the array length plus -2.  
document.write (ar.indexOf("ab", -2) + "<br/>");  
// Output: 3  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Métodos (JavaScript)](../../javascript/reference/javascript-methods.md)   
 [Objeto Array](../../javascript/reference/array-object-javascript.md)   
 [Usando matrizes](../../javascript/advanced/using-arrays-javascript.md)