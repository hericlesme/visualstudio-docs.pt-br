---
title: Objeto Int8Array | Microsoft Docs
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
ms.assetid: 0e3bdbc5-8d85-4c0d-b399-693b01674803
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e3f85a505f41f2909330e938f4978433fc823f9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637786"
---
# <a name="int8array-object"></a>Objeto Int8Array
Uma matriz tipada de valores inteiros de 8 bits. O conteúdo é inicializado em 0. Se o número de bytes solicitado não puder ser alocado, uma exceção será gerada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
      int8Array = new Int8Array( length );  
intArray = new Int8Array( array );  
intArray = new Int8Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `int8Array`  
 Obrigatório. O nome da variável à qual o objeto `Int8Array` é atribuído.  
  
 `length`  
 Especifica o número de elementos na matriz.  
  
 `array`  
 A matriz (ou matriz tipada) que está contida nesta matriz. O conteúdo é inicializado no conteúdo da matriz especificada ou da matriz tipada, com cada elemento convertido para o tipo Int8.  
  
 `buffer`  
 O ArrayBuffer que Int8Array representa.  
  
 `byteOffset`  
 Opcional. Especifica o deslocamento em bytes desde o início do buffer no qual Int8Array deve começar.  
  
 `length`  
 O número de elementos na matriz.  
  
## <a name="constants"></a>Constantes  
 A tabela a seguir lista as constantes do objeto `Int8Array`.  
  
|Constante|Descrição|  
|--------------|-----------------|  
|[Constante BYTES_PER_ELEMENT](../../javascript/reference/bytes-per-element-constant-int8array.md)|O tamanho em bytes de cada elemento da matriz.|  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir lista as constantes do objeto `Int8Array`.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|[Propriedade buffer](../../javascript/reference/buffer-property-int8array.md)|Somente leitura. Obtém o ArrayBuffer que é referenciado por essa matriz.|  
|[Propriedade byteLength](../../javascript/reference/bytelength-property-int8array.md)|Somente leitura. O comprimento dessa matriz desde o início de seu ArrayBuffer, em bytes, fixado na ocasião da construção.|  
|[Propriedade byteOffset](../../javascript/reference/byteoffset-property-int8array.md)|Somente leitura. O deslocamento dessa matriz desde o início de seu ArrayBuffer, em bytes, fixado na ocasião da construção.|  
|[Propriedade Length](../../javascript/reference/length-property-int8array.md)|O comprimento da matriz.|  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos do objeto `Int8Array`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Set (Int8Array)](../../javascript/reference/set-method-int8array.md)|Define um valor ou uma matriz de valores.|  
|[Método subarray (Int8Array)](../../javascript/reference/subarray-method-int8array.md)|Obtém uma nova exibição de Int8Array do repositório de ArrayBuffer para essa matriz.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar um objeto Int8Array para processar os dados binários adquiridos de um XmlHttpRequest:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int8Array(buffer.byteLength);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt8(i);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]