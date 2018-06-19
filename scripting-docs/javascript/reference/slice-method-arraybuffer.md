---
title: Método slice (ArrayBuffer) | Microsoft Docs
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
ms.assetid: 2dcc51ff-f444-4d51-80ba-3bcd845ba0ae
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25fc10a02b4a3422a6720ad91c8bba29906da0e5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640486"
---
# <a name="slice-method-arraybuffer"></a>Método slice (ArrayBuffer)
Retorna uma seção de um [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
arrayBufferObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `arrayBufferObj`  
 Necessário. O [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) objeto será copiada da seção.  
  
 `start`  
 Necessário. O índice de bytes do início da seção a ser copiado.  
  
 `end`  
 Opcional. O índice de bytes do final da seção a ser copiado.  
  
## <a name="remarks"></a>Comentários  
 O `slice` método retorna um [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) objeto que contém a parte especificada de `arrayBufferObj`.  
  
 O método `slice` copia tudo até o byte indicado por `end`, mas não o inclui. Se `start` ou `end` é negativo, o índice especificado é tratado como `length`  +  `start` ou `end`, respectivamente, onde `length` é o comprimento do [ArrayBuffer](../../javascript/reference/arraybuffer-object.md). Se `end` for omitido, a extração continua até o final de `arrayBufferObj`. Se `end` ocorre antes de `start`, nenhum byte é copiado para o novo [ArrayBuffer](../../javascript/reference/arraybuffer-object.md).  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir mostram como usar o método `slice`.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer1 = req.response;  
            var buffer2 = buffer1.slice(40, 48);  
            var dataview = new DataView(buffer2);  
            var ints = new Int32Array(buffer2.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[1]);  
        }  
    }  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Objeto ArrayBuffer](../../javascript/reference/arraybuffer-object.md)