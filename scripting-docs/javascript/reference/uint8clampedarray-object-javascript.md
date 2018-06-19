---
title: Objeto Uint8ClampedArray (JavaScript) | Microsoft Docs
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
ms.assetid: 0c5537f7-00b4-487a-8fba-ef032e67e7bd
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51673eadc8eb905355bf136dc82b2f240462180a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24642106"
---
# <a name="uint8clampedarray-object-javascript"></a>Objeto Uint8ClampedArray (JavaScript)
Uma matriz tipada de valores inteiros sem sinal de 8 bits com valores fixados no intervalo 0-255. O conteúdo é inicializado em 0. Se não é possível designar o número de bytes solicitado, uma exceção é gerada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
      uint8ClampedArray = new Uint8ClampedArray( length );  
uint8ClampedArray = new Uint8ClampedArray( array );  
uint8ClampedArray = new Uint8ClampedArray( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `uint8ClampedArray`  
 Obrigatório. O nome da variável à qual o objeto `Uint8ClampedArray` é atribuído.  
  
 `length`  
 Opcional. O número de elementos na matriz.  
  
 `array`  
 Opcional. A matriz (ou matriz tipada) que essa matriz contém. O conteúdo é inicializado no conteúdo da matriz especificada ou da matriz tipada, com cada elemento convertido no tipo `Uint8`.  
  
 `buffer`  
 Opcional. O [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) que o `Uint8ClampedArray` representa.  
  
 `byteOffset`  
 Opcional. O deslocamento, em bytes, desde o início do buffer no qual `Uint8ClampedArray` deve começar.  
  
 `length`  
 Opcional. O número de elementos na matriz.  
  
## <a name="remarks"></a>Comentários  
 Os valores armazenados em um objeto `Uint8ClampedArray` estão entre 0 e 255. Se você definir um valor negativo para um membro da matriz, 0 é definido como valor. Se você definir um valor superior a 255, 255 é definido como valor.  
  
 Valores em uma `Uint8ClampedArray` objeto são arredondados para o mesmo valor, mais próximo que é chamada de arredondamento bancário.  
  
## <a name="constants"></a>Constantes  
 A tabela a seguir lista as constantes do objeto `Uint8ClampedArray`.  
  
|Constante|Descrição|  
|--------------|-----------------|  
|[Constante BYTES_PER_ELEMENT](../../javascript/reference/bytes-per-element-constant-uint8clampedarray.md)|O tamanho, em bytes, de cada elemento da matriz.|  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir lista as constantes do objeto `Uint8ClampedArray`.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|[Propriedade buffer](../../javascript/reference/buffer-property-uint8clampedarray.md)|Somente leitura. Obtém o [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) que é referenciado por essa matriz.|  
|[Propriedade byteLength](../../javascript/reference/bytelength-property-uint8clampedarray.md)|Somente leitura. O comprimento dessa matriz desde o início do seu [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), em bytes, como fixo no tempo de construção.|  
|[Propriedade byteOffset](../../javascript/reference/byteoffset-property-uint8clampedarray.md)|Somente leitura. O deslocamento dessa matriz desde o início do seu [ArrayBuffer](../../javascript/reference/arraybuffer-object.md), em bytes, como fixo no tempo de construção.|  
|[Propriedade Length](../../javascript/reference/length-property-uint8clampedarray.md)|O comprimento da matriz.|  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos do objeto `Uint8ClampedArray`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Set](../../javascript/reference/set-method-uint8clampedarray.md)|Define um valor ou uma matriz de valores.|  
|[Método subarray](../../javascript/reference/subarray-method-uint8clampedarray.md)|Obtém uma nova `Uint8ClampedArray` exibir o [ArrayBuffer](../../javascript/reference/arraybuffer-object.md) armazenar para essa matriz, especificando os elementos e o sobrenome da submatriz.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar um objeto `Uint8ClampedArray` para processar os dados binários adquiridos de um `XmlHttpRequest`:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Uint8ClampedArray(buffer.byteLength);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getUint8(i);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como os valores são restritos em um `Uint8ClampedArray`.  
  
```JavaScript  
var ints = new Uint8ClampedArray(2);  
ints[0] = -1;  // 0 will be assigned.  
ints[1] = 256; // 255 will be assigned.  
  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como os valores são arredondados em um `Uint8ClampedArray`.  
  
```  
var ints = new Uint8ClampedArray(4);  
ints[0] = 11.3; // 11 will be assigned (same as Int8Array).  
ints[1] = 11.8; // 12 will be assigned (same as Int8Array).  
ints[2] = 10.5; // 10 will be assigned (rounded to the nearest   
                // even value).  
ints[3] = 11.5; // 12 will be assigned (rounded to the nearest   
                // even value).  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Uint8Array](../../javascript/reference/uint8array-object.md)   
 [Objeto ArrayBuffer](../../javascript/reference/arraybuffer-object.md)
