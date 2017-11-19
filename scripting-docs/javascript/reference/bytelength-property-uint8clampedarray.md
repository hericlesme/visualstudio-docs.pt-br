---
title: Propriedade (Uint8ClampedArray) byteLength | Microsoft Docs
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
ms.assetid: 37ae1728-8e2c-496c-bb77-f5f85b1ecbba
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a949f245b0710e4c44c7a5944869eca4ea146375
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="bytelength-property-uint8clampedarray"></a>Propriedade byteLength (Uint8ClampedArray)
Somente leitura. O comprimento dessa matriz desde o início do seu [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), em bytes, como fixo no tempo de construção.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
var arrayByteLength = uint8ClampedArray.byteLength;  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como obter o tamanho da matriz.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Uint8ClampedArray(buffer.byteLength);  
            alert(intArr.byteLength);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Objeto ArrayBuffer](../../javascript/reference/arraybuffer-object.md)   
 [Objeto Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)