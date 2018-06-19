---
title: Função array IsArray (JavaScript) | Microsoft Docs
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
- isArray function [JavaScript]
- Array.isArray function [JavaScript]
ms.assetid: 58f7d2e0-d310-4292-b9bc-37a73c585780
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c31bdfe022cd41648117fc80c8df257e48e592ae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633466"
---
# <a name="arrayisarray-function-javascript"></a>Função Array.isArray (JavaScript)
Determina se um objeto é uma matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Array.isArray(object)   
```  
  
#### <a name="parameters"></a>Parâmetros  
 `object`  
 Necessário. O objeto a ser testado.  
  
## <a name="return-value"></a>Valor de retorno  
 `true` se `object` for uma matriz. Caso contrário, `false`. Se o argumento `object` não for um objeto, `false` será retornado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da função `Array.isArray`.  
  
```JavaScript  
var ar = [];  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = new Array();  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = [1, 2, 3];  
var result = Array.isArray(ar);  
// Output: true  
  
var result = Array.isArray("an array");  
document.write(result);  
// Output: false  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Array](../../javascript/reference/array-object-javascript.md)   
 [Usando matrizes](../../javascript/advanced/using-arrays-javascript.md)   
 [Operador TypeOf](../../javascript/reference/typeof-operator-decrementjavascript.md)