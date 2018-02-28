---
title: "Método slice (matriz) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- slice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- zero-based index
- Array object
- slice method
ms.assetid: 3c122219-14de-4126-b091-809659c026d6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a61cd331abef9d1a0d979f547f6d6f12222c1eee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="slice-method-array-javascript"></a>Método slice (Array) (JavaScript)
Retorna uma seção de uma matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
arrayObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `arrayObj`  
 Necessário. Um objeto `Array`.  
  
 `start`  
 Necessário. O início da parte especificada de `arrayObj`.  
  
 `end`  
 Opcional. O fim da parte especificada de `arrayObj`.  
  
## <a name="remarks"></a>Comentários  
 O `slice` método retorna um `Array` objeto que contém a parte especificada de `arrayObj`.  
  
 O `slice` método copia até, mas não incluindo, o elemento indicado pelo `end`. Se `start` é negativo, ele será tratado como `length`  +  `start`, onde `length` é o comprimento da matriz. Se `end` é negativo, ele será tratado como `length`  +  `end` onde `length` é o comprimento da matriz. Se `end` for omitido, a extração continua até o final de `arrayObj`. Se `end` ocorre antes de `start`, não há elementos são copiados para a nova matriz.  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir mostram como usar o método `slice`. No primeiro exemplo, todos, exceto o último elemento de `myArray` é copiado para `newArray`. No segundo exemplo, os dois últimos elementos de `myArray` são copiados para `newArray`.  
  
```JavaScript  
var origArray = [3, 5, 7, 9];  
var newArray = origArray. slice(0, -1);  
document.write(origArray);  
document.write("<br/>");  
newArray = origArray. slice(-2);  
document.write(newArray);  
  
// Output:  
// 3,5,7,9  
// 7,9  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [dividir o método (String)](../../javascript/reference/slice-method-string-javascript.md)   
 [Objeto String](../../javascript/reference/string-object-javascript.md)