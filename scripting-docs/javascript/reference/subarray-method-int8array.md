---
title: Método (Int8Array) subarray | Microsoft Docs
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
ms.assetid: 46271ed6-a3c3-41fb-bd6f-81efa9e8dedc
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e32c3a0da7e3173273eb40bf52bb6583bd77df51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640006"
---
# <a name="subarray-method-int8array"></a>Método subarray (Int8Array)
Obtém uma nova exibição de Int8Array do repositório ArrayBuffer para essa matriz, fazendo referência aos elementos em begin (inclusive) até end (exclusive).  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
var newInt8Array = int8Array.subset(begin, end);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `newInt8Array`  
 A submatriz retornada por este método.  
  
 `begin`  
 O índice do início da matriz.  
  
 `end`  
 O índice do final da matriz. Ele não é inclusivo.  
  
## <a name="remarks"></a>Comentários  
 Se begin ou end for negativo, ele fará referência a um índice no final da matriz, em vez de no início. Se end não for especificado, a submatriz conterá todos os elementos desde o begin até o final da matriz tipada. O intervalo especificado pelos valores de begin e end é fixado ao intervalo de índice válido para a matriz atual. Se o comprimento calculado do novo TypedArray for negativo, ele será fixado como zero. O TypedArray retornado será do mesmo tipo da matriz na qual esse método é invocado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como obter uma submatriz de dois elementos, começando com o primeiro elemento dessa matriz.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Int8Array(buffer.byteLength);  
            var subArr = intArr.subarray(0, 2);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]