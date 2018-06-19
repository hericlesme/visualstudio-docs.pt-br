---
title: Método (Uint8ClampedArray) subarray | Microsoft Docs
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
ms.assetid: 309ed9e8-5805-47ab-b3ed-501cae1323dd
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76cda8b123b02b4c19a7fd162f3bfbce4540d149
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640546"
---
# <a name="subarray-method-uint8clampedarray"></a>Método subarray (Uint8ClampedArray)
Obtém uma nova [Uint8ClampedArray](../../javascript/reference/uint8array-object.md) exibir o [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) armazenar para essa matriz, especificando o primeiro e o último membro da submatriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
var newUint8ClampedArray = uint8ClampedArray.subarray(begin, end);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `newUint8ClampedArray`  
 Obrigatório. A submatriz retornada por este método.  
  
 `begin`  
 Opcional. O índice do início da matriz.  
  
 `end`  
 Opcional. O índice do final da matriz. Ele não é inclusivo.  
  
## <a name="remarks"></a>Comentários  
 Se `begin` ou `end` for negativo, a referência será a um índice do final da matriz, e não do início. Se `end` não for especificado, a submatriz conterá todos os elementos de `begin` até o final da matriz digitada. O intervalo especificado pelos valores de `begin` e `end` é fixado ao intervalo válido do índice para a matriz atual. Se o tamanho calculado da nova matriz digitada for negativo, ele será fixado como zero. A matriz retornada tem o mesmo tipo que a matriz na qual esse método é invocado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como obter uma submatriz com dois elementos, começando com o primeiro elemento da matriz.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Uint8Array](../../javascript/reference/uint8array-object.md)   
 [Objeto ArrayBuffer](../../javascript/reference/arraybuffer-object.md)   
 [Objeto Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)