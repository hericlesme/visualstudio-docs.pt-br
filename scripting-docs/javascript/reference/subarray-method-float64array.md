---
title: "Método (Float64Array) subarray | Microsoft Docs"
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
ms.assetid: f3c24e1b-5fb2-49a1-8183-0fda33dbeaba
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08f72854b9dc87394bdce2552d5d48ff4b1270f8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="subarray-method-float64array"></a>Método subarray (Float64Array)
Obtém uma nova exibição Float64Array do [ArrayBuffer Object](../../javascript/reference/arraybuffer-object.md) armazenar para essa matriz, especificando o primeiro e o último membro da submatriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
var newFloat64Array = float64Array.subarray(begin, end);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `newFloat64Array`  
 A submatriz retornada por este método.  
  
 `begin`  
 O índice do início da matriz.  
  
 `end`  
 O índice do final da matriz.  
  
## <a name="remarks"></a>Comentários  
 Se `begin` ou `end` for negativo, a referência será a um índice do final da matriz, e não do início. Se `end` não for especificado, a submatriz conterá todos os elementos de `begin` até o final da matriz digitada. O intervalo especificado pelos valores de `begin` e `end` é fixado ao intervalo válido do índice para a matriz atual. Se o tamanho calculado da nova matriz digitada for negativo, ele será fixado como zero. A matriz retornada é do mesmo tipo da matriz na qual esse método é invocado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como obter uma submatriz três elementos, começando com o primeiro elemento da matriz.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var floatArr = new Float64Array(buffer.byteLength / 8);  
            var subArr = floatArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]