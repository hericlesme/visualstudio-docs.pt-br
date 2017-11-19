---
title: "Método unshift (Array) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: unshift
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: unshift method
ms.assetid: 8c6a39ed-bab3-4ca4-9350-571a9427ec94
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c3f0d210514d04afa5cf467819a5e843925e1a68
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="unshift-method-array-javascript"></a>Método unshift (Array) (JavaScript)
Insere novos elementos no início de uma matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
arrayObj.unshift([item1[, item2 [, . . . [, itemN]]]])  
```  
  
## <a name="parameters"></a>Parâmetros  
 `arrayObj`  
 Necessário. Um objeto `Array`.  
  
 `item1, item2,. . ., itemN`  
 Opcional. Elementos para inserir no início de `Array`.  
  
## <a name="remarks"></a>Comentários  
 O `unshift` método insere elementos no início de uma matriz, para que elas apareçam na mesma ordem em que aparecem na lista de argumentos.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `unshift`.  
  
```JavaScript  
var ar = new Array();  
ar.unshift(10, 11);  
ar.unshift(12, 13, 14);  
document.write(ar.toString());  
  
// Output: 12,13,14,10,11  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método shift (Array)](../../javascript/reference/shift-method-array-javascript.md)