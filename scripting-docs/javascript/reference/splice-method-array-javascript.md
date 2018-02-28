---
title: "Método splice (Array) (JavaScript) | Microsoft Docs"
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
- splice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- splice method
ms.assetid: 85fdfb13-e3d9-4c89-b524-3ccee7001c93
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d56a22244f76f5ce7221c276629907811733d51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="splice-method-array-javascript"></a>Método splice (Array) (JavaScript)
Remove elementos de uma matriz e, se necessário, insere novos elementos em seu local, retornando os elementos excluídos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
arrayObj.splice(start, deleteCount, [item1[, item2[, . . . [,itemN]]]])  
```  
  
## <a name="parameters"></a>Parâmetros  
 `arrayObj`  
 Necessário. Um objeto `Array`.  
  
 `start`  
 Necessário. O local com base em zero na matriz da qual iniciar a remoção de elementos.  
  
 `deleteCount`  
 Necessário. O número de elementos a serem removidos.  
  
 `item1, item2,. . ., itemN`  
 Opcional. Elementos para inserir a matriz em vez dos elementos excluídos.  
  
## <a name="remarks"></a>Comentários  
 O `splice` método modifica `arrayObj` , removendo o número especificado de elementos de posição `start` e inserindo novos elementos. Os elementos excluídos são retornados como um novo `Array` objeto.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como usar o método `splice`.  
  
```JavaScript  
var arr = new Array("4", "11", "2", "10", "3", "1");  
arr.splice(2, 2, "21", "31");  
document.write(arr);  
  
// Output: 4,11,21,31,3,1  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método slice (Array)](../../javascript/reference/slice-method-array-javascript.md)