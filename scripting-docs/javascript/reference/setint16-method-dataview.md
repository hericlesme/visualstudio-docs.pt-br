---
title: "Método setInt16 (DataView) | Microsoft Docs"
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
ms.assetid: 901c6cf5-63fb-45bd-9ea8-185c1d892060
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04ea20079c217d1aeef8456e9c81996661fed356
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="setint16-method-dataview"></a>Método setInt16 (DataView)
Define o valor Int16 no deslocamento de byte especificado desde o início do modo de exibição. Não há nenhuma restrição de alinhamento. valores de vários bytes podem ser definidos no deslocamento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
dataView.setInt16(byteOffset, value, littleEndian);   
```  
  
## <a name="parameters"></a>Parâmetros  
 `byteOffset`  
 O local no buffer no qual o valor deve ser recuperado.  
  
 `value`  
 O valor a ser definido.  
  
 `littleEndian`  
 Opcional. Se for false ou indefinido, um valor de big-endian deve ser gravado, caso contrário, um valor de little endian deve ser gravado.  
  
## <a name="remarks"></a>Comentários  
 Esses métodos de geram uma exceção se escrevem além do fim do modo de exibição.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como definir a primeira Int16 em DataView.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setInt16(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]