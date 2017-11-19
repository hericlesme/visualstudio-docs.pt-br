---
title: "Método Sort (Array) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: sort
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Sort method
ms.assetid: 9bd8b54a-c838-4806-85c8-62eebe6bc48c
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d098b47591ca7bbb4e3e8da5e5c14f8c0e9b255
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="sort-method-array-javascript"></a>Método sort (Array) (JavaScript)
Classifica um `Array`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
arrayobj.sort(sortFunction)   
```  
  
## <a name="parameters"></a>Parâmetros  
 `arrayObj`  
 Necessário. Qualquer objeto `Array`.  
  
 `sortFunction`  
 Opcional. O nome da função usada para determinar a ordem dos elementos. Se omitido, os elementos são classificados em ordem de caractere ASCII, crescente.  
  
## <a name="return-value"></a>Valor de retorno  
 A matriz classificada.  
  
## <a name="remarks"></a>Comentários  
 O `sort` método classifica o `Array` objeto no local; nenhum novo `Array` objeto é criado durante a execução.  
  
 Se você fornecer uma função de `sortFunction` argumento, ele deve retornar um dos seguintes valores:  
  
-   Um valor negativo se o primeiro argumento passado é menor que o segundo argumento.  
  
-   Zero se os dois argumentos são equivalentes.  
  
-   Um valor positivo se o primeiro argumento for maior que o segundo argumento.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o método `sort`.  
  
```JavaScript  
var a = new Array(4, 11, 2, 10, 3, 1);  
  
var b = a.sort();  
document.write(b);  
document.write("<br/>");  
  
// This is ASCII character order.  
// Output: 1,10,11,2,3,4)  
  
// Sort the array elements with a function that compares array elements.  
b = a.sort(CompareForSort);  
document.write(b);  
document.write("<br/>");  
// Output: 1,2,3,4,10,11.  
  
// Sorts array elements in ascending order numerically.  
function CompareForSort(first, second)  
{  
    if (first == second)  
        return 0;  
    if (first < second)  
        return -1;  
    else  
        return 1;   
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]