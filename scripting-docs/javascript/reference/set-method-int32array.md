---
title: "definir o método (Int32Array) | Microsoft Docs"
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
ms.assetid: c0716454-88dc-43d5-8ce9-f8fdc91da4c5
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 033c2ba996b5754ec15eb97d9926f20a88c0dc6e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="set-method-int32array"></a>Método Set (Int32Array)
Define um valor ou uma matriz de valores.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
Int32Array.set(index, value);  
int32Array.set(array, offset);  
  
```  
  
## <a name="parameters"></a>Parâmetros  
 `index`  
 O índice do local a ser definido.  
  
 `value`  
 O valor a ser definido.  
  
 `array`  
 Uma matriz tipada ou não tipada de valores a serem definidos.  
  
 `offset`  
 O índice na matriz atual em que os valores devem ser gravados.  
  
## <a name="remarks"></a>Comentários  
 Se a matriz de entrada for um TypedArray, as duas matrizes poderão usar o mesmo ArrayBuffer subjacente. Nesta situação, a definição dos valores ocorrerá se todos os dados forem copiados primeiro para um buffer temporário que não se sobrepõe a nenhuma das matrizes e se, em seguida, os dados do buffer temporário forem copiados para a matriz atual.  
  
 Se o deslocamento mais o tamanho da matriz especificada estiver fora do intervalo para o TypedArray atual, uma exceção será gerada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como definir o primeiro elemento da matriz.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var intArr = new Int32Array(buffer.byteLength / 4);  
            intArr.set(0, 9);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]