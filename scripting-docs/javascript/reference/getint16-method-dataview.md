---
title: "Método getInt16 (DataView) | Microsoft Docs"
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
ms.assetid: d364cbe0-48a6-4350-a6ca-9f563d7ae571
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a30804ddaa4840bfbd8a791ac5a5d4d82d107879
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="getint16-method-dataview"></a>Método getInt16 (DataView)
Obtém o valor Int16 no deslocamento de byte especificado desde o início do modo de exibição. Não há nenhuma restrição de alinhamento. valores de vários bytes podem ser obtidos de deslocamento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
var testInt = dataView.getInt16(byteOffset, littleEndian);   
```  
  
## <a name="parameters"></a>Parâmetros  
 `testInt`  
 Necessário. O valor Int16 que é retornado do método.  
  
 `byteOffset`  
 O local no buffer no qual o valor deve ser recuperado.  
  
 `littleEndian`  
 Opcional. Se for false ou indefinido, um valor de big-endian deve ser lido, caso contrário, um valor de little endian deve ser lido.  
  
## <a name="remarks"></a>Comentários  
 Esses métodos de geram uma exceção se eles seriam ler além do fim do modo de exibição.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como obter o primeiro Int16 em DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            alert(dataView.getInt16(0));  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]