---
title: Objeto Uint32Array | Microsoft Docs
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
ms.assetid: c4bf5409-2d4b-4660-9f4b-a45d7a02b47e
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05f185e02ac117491d067ddca6605197d126620e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="uint32array-object"></a>Objeto Uint32Array
Uma matriz tipada de valores inteiros sem sinal de 32 bits. O conteúdo é inicializado em 0. Se o número de bytes solicitado não puder ser alocado, uma exceção será gerada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
      uint32Array = new Uint32Array( length );  
uint32Array = new Uint32Array( array );  
uint32Array = new Uint32Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `uint32Array`  
 Necessário. O nome da variável à qual o **Uint32Array** objeto será atribuído.  
  
 `length`  
 Especifica o número de elementos na matriz.  
  
 `array`  
 A matriz (ou matriz tipada) que está contida nesta matriz. O conteúdo é inicializado no conteúdo da matriz especificada ou da matriz tipada, com cada elemento convertido para o tipo Uint32.  
  
 `buffer`  
 O ArrayBuffer que Uint32Array representa.  
  
 `byteOffset`  
 Opcional. Especifica o deslocamento em bytes desde o início do buffer no qual Uint32Array deve começar.  
  
 `length`  
 O número de elementos na matriz.  
  
## <a name="constants"></a>Constantes  
 A tabela a seguir lista as constantes do objeto `Uint32Array`.  
  
|Constante|Descrição|  
|--------------|-----------------|  
|[Constante BYTES_PER_ELEMENT](../../javascript/reference/bytes-per-element-constant-uint32array.md)|O tamanho em bytes de cada elemento da matriz.|  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir lista as constantes do objeto `Uint32Array`.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|[Propriedade buffer](../../javascript/reference/buffer-property-uint32array.md)|Somente leitura. Obtém o ArrayBuffer que é referenciado por essa matriz.|  
|[Propriedade byteLength](../../javascript/reference/bytelength-property-uint32array.md)|Somente leitura. O comprimento dessa matriz desde o início de seu ArrayBuffer, em bytes, fixado na ocasião da construção.|  
|[Propriedade byteOffset](../../javascript/reference/byteoffset-property-uint32array.md)|Somente leitura. O deslocamento dessa matriz desde o início de seu ArrayBuffer, em bytes, fixado na ocasião da construção.|  
|[Propriedade Length](../../javascript/reference/length-property-uint32array.md)|O comprimento da matriz.|  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos do objeto `Uint32Array`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Set (Uint32Array)](../../javascript/reference/set-method-uint32array.md)|Define um valor ou uma matriz de valores.|  
|[Método subarray (Uint32Array)](../../javascript/reference/subarray-method-uint32array.md)|Obtém uma nova exibição de Uint32Array do repositório de ArrayBuffer para essa matriz.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar um objeto Uint32Array para processar os dados binários adquiridos de um XMLHttpRequest:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]