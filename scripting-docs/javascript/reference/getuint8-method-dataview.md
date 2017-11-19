---
title: "Método getUint8 (DataView) | Microsoft Docs"
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
ms.assetid: 9fbf4be3-4c0b-4963-a7a1-d57f1501b4cf
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 315baa2ca5abfe006a7f8d524619479d99a11fc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="getuint8-method-dataview"></a>Método getUint8 (DataView)
Obtém o valor Uint8 no deslocamento de byte especificado desde o início do modo de exibição. Não há nenhuma restrição de alinhamento. valores de vários bytes podem ser obtidos de deslocamento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
var testInt = dataView.getUint8(byteOffset);   
```  
  
## <a name="parameters"></a>Parâmetros  
 `testInt`  
 Necessário. O valor Uint8 que é retornado do método.  
  
 `byteOffset`  
 O local no buffer no qual o valor deve ser recuperado.  
  
## <a name="remarks"></a>Comentários  
 Esses métodos de geram uma exceção se eles seriam ler além do fim do modo de exibição.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como obter o primeiro Uint8 em DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getUint8(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]