---
title: Objeto Float64Array | Microsoft Docs
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
ms.assetid: 74c945dc-56ae-458c-b0aa-782f240e9b6c
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20544812d94c1234d85d714f6e469d0de4f4c5ab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="float64array-object"></a>Objeto Float64Array
Uma matriz tipada de valores float de 64 bits. O conteúdo é inicializado em 0. Se o número de bytes solicitado não puder ser alocado, uma exceção será gerada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
      float64Array = new Float64Array( length );  
float64Array = new Float64Array( array );  
float64Array = new Float64Array( buffer, byteOffset, length);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `float64Array`  
 Necessário. O nome da variável à qual o **Float64Array** objeto será atribuído.  
  
 `length`  
 Especifica o número de elementos na matriz.  
  
 `array`  
 A matriz (ou matriz tipada) que está contida nesta matriz. O conteúdo é inicializado no conteúdo da matriz especificada ou da matriz digitada, com cada elemento convertido para o tipo Float64.  
  
 `buffer`  
 O ArrayBuffer que Float64Array representa.  
  
 `byteOffset`  
 Opcional. Especifica o deslocamento em bytes desde o início do buffer no qual Float64Array deve começar.  
  
 `length`  
 O número de elementos na matriz.  
  
## <a name="constants"></a>Constantes  
 A tabela a seguir lista as constantes do objeto `Float64Array`.  
  
|Constante|Descrição|  
|--------------|-----------------|  
|[Constante BYTES_PER_ELEMENT](../../javascript/reference/bytes-per-element-constant-float64array.md)|O tamanho em bytes de cada elemento da matriz.|  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir lista as constantes do objeto `Float64Array`.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|[Propriedade buffer](../../javascript/reference/bytelength-property-float64array.md)|Somente leitura. Obtém o ArrayBuffer que é referenciado por essa matriz.|  
|[Propriedade byteLength](../../javascript/reference/bytelength-property-float64array.md)|Somente leitura. O comprimento dessa matriz desde o início de seu ArrayBuffer, em bytes, fixado na ocasião da construção.|  
|[Propriedade byteOffset](../../javascript/reference/length-property-float64array.md)|Somente leitura. O deslocamento dessa matriz desde o início de seu ArrayBuffer, em bytes, fixado na ocasião da construção.|  
|[Propriedade Length](../../javascript/reference/length-property-float64array.md)|O comprimento da matriz.|  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos do objeto `Float64Array`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Get](../../javascript/reference/get-method-float64array.md)|Pode ser omitido. Obtém o elemento no índice especificado.|  
|[Método Set (Float64Array)](../../javascript/reference/set-method-float64array.md)|Define um valor ou uma matriz de valores.|  
|[Método subarray (Float64Array)](../../javascript/reference/subarray-method-float64array.md)|Obtém uma nova exibição de Float64Array do repositório de ArrayBuffer para essa matriz.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar um objeto Float64Array para processar os dados binários adquiridos de um XmlHttpRequest:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Float64Array(buffer.byteLength / 8);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getFloat64(i * 8);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]