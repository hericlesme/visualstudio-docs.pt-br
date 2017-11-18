---
title: Objeto Uint16Array | Microsoft Docs
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
ms.assetid: e684647d-04d0-41a9-9089-16612e18ec7d
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 447c0509a29f1696e0204d6f37ff88d3c0bdecae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="uint16array-object"></a>Objeto Uint16Array
Uma matriz tipada de valores inteiros sem sinal de 16 bits. O conteúdo é inicializado em 0. Se o número de bytes solicitado não puder ser alocado, uma exceção será gerada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
      uint16Array = new Uint16Array( length );  
uint16Array = new Uint16Array( array );  
uint16Array = new Uint16Array( buffer, byteOffset, length );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `uint16Array`  
 Necessário. O nome da variável à qual o **Uint16Array** objeto será atribuído.  
  
 `length`  
 Especifica o número de elementos na matriz.  
  
 `array`  
 A matriz (ou matriz tipada) que está contida nesta matriz. O conteúdo é inicializado no conteúdo da matriz especificada ou da matriz tipada, com cada elemento convertido para o tipo Uint16.  
  
 `buffer`  
 O ArrayBuffer que Uint16Array representa.  
  
 `byteOffset`  
 Opcional. Especifica o deslocamento em bytes desde o início do buffer no qual Uint16Array deve começar.  
  
 `length`  
 O número de elementos na matriz.  
  
## <a name="constants"></a>Constantes  
 A tabela a seguir lista as constantes do objeto `Uint16Array`.  
  
|Constante|Descrição|  
|--------------|-----------------|  
|[Constante BYTES_PER_ELEMENT](../../javascript/reference/bytes-per-element-constant-uint16array.md)|O tamanho em bytes de cada elemento da matriz.|  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir lista as constantes do objeto `Uint16Array`.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|[Propriedade buffer](../../javascript/reference/buffer-property-uint16array.md)|Somente leitura. Obtém o ArrayBuffer que é referenciado por essa matriz.|  
|[Propriedade byteLength](../../javascript/reference/bytelength-property-uint16array.md)|Somente leitura. O comprimento dessa matriz desde o início de seu ArrayBuffer, em bytes, fixado na ocasião da construção.|  
|[Propriedade byteOffset](../../javascript/reference/byteoffset-property-uint16array.md)|Somente leitura. O deslocamento dessa matriz desde o início de seu ArrayBuffer, em bytes, fixado na ocasião da construção.|  
|[Propriedade Length](../../javascript/reference/length-property-uint16array.md)|O comprimento da matriz.|  
|||  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos do objeto `Uint16Array`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Set (Uint16Array)](../../javascript/reference/set-method-uint16array.md)|Define um valor ou uma matriz de valores.|  
|[Método subarray (Uint16Array)](../../javascript/reference/subarray-method-uint16array.md)|Obtém uma nova exibição de Uint16Array do repositório de ArrayBuffer para essa matriz.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar um objeto Uint16Array para processar os dados binários adquiridos de um XmlHttpRequest:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint16Array(buffer.byteLength / 2);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint16(i * 2);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]