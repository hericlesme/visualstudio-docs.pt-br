---
title: Método setUint16 (DataView) | Microsoft Docs
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
ms.assetid: bdf47cda-7fa5-4aaa-8aa2-8cf9a8d56cb3
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 935c117995e00284a0083a6bdf7aedfc8c51d15c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639696"
---
# <a name="setuint16-method-dataview"></a>Método setUint16 (DataView)
Define o valor Uint16 no deslocamento de byte especificado desde o início do modo de exibição. Não há nenhuma restrição de alinhamento. valores de vários bytes podem ser definidos no deslocamento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
dataView.setUint16(byteOffset, value, littleEndian);   
```  
  
## <a name="parameters"></a>Parâmetros  
 `testInt`  
 Necessário. O valor Uint16 que é retornado do método.  
  
 `value`  
 O valor a ser definido.  
  
 `byteOffset`  
 O local no buffer no qual o valor deve ser recuperado.  
  
 `littleEndian`  
 Opcional. Se for false ou indefinido, um valor de big-endian deve ser gravado, caso contrário, um valor de little endian deve ser gravado.  
  
## <a name="remarks"></a>Comentários  
 Esses métodos de geram uma exceção se escrevem além do fim do modo de exibição.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como definir a primeira Uint16 em DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setUint16(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]