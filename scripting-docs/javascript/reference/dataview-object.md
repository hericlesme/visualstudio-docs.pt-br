---
title: Objeto DataView | Microsoft Docs
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
ms.assetid: 250ec067-7505-4ee0-82ab-bfd3c2820afa
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 370ee1afbdf7fe1d87843c4979833d54a575a4fd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637266"
---
# <a name="dataview-object"></a>Objeto DataView
Você pode usar um objeto de DataView para ler e gravar os diferentes tipos de dados binários em qualquer parte do arraybuffer.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
dataView = new DataView(buffer, byteOffset, byteLength);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dataView`  
 Necessário. O nome da variável à qual o **DataView** objeto será atribuído.  
  
 `buffer`  
 Parte do ArrayBuffer que representa a exibição de dados.  
  
 `byteOffset`  
 Opcional. Especifica o deslocamento em bytes do início do buffer em que a exibição de dados deve começar.  
  
 `byteLength`  
 Opcional. Especifica o comprimento (em bytes) da seção de buffer que deve representar a exibição de dados.  
  
## <a name="remarks"></a>Comentários  
 Se ambos byteOffset e byteLength forem omitidos, a exibição de dados abrange todo o intervalo de ArrayBuffer. Se o byteLength for omitido, a exibição de dados se estende do byteOffset a determinada até o fim da parte do ArrayBuffer. Se o determinado byteOffset e byteLength faz referência a uma área além do fim da parte do ArrayBuffer, uma exceção será gerada.  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir lista as propriedades do objeto `DataView`.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|[Propriedade buffer](../../javascript/reference/buffer-property-dataview.md)|Somente leitura. Obtém o ArrayBuffer que é referenciado por esta exibição.|  
|[Propriedade byteLength](../../javascript/reference/bytelength-property-dataview.md)|Somente leitura. O comprimento dessa exibição desde o início de seu ArrayBuffer, em bytes, fixado na ocasião da construção.|  
|[Propriedade byteOffset](../../javascript/reference/byteoffset-property-dataview.md)|Somente leitura. O deslocamento dessa exibição desde o início do seu ArrayBuffer, em bytes, como fixo no tempo de construção.|  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos do objeto `DataView`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método getInt8](../../javascript/reference/getint8-method-dataview.md)|Obtém o valor Int8 no deslocamento de byte especificado desde o início do modo de exibição.|  
|[Método getUint8 (DataView)](../../javascript/reference/getuint8-method-dataview.md)|Obtém o valor Uint8 no deslocamento de byte especificado desde o início do modo de exibição.|  
|[Método getInt16 (DataView)](../../javascript/reference/getint16-method-dataview.md)|Obtém o valor Int16 no deslocamento de byte especificado desde o início do modo de exibição.|  
|[Método getUint16 (DataView)](../../javascript/reference/getuint16-method-dataview.md)|Obtém o valor Uint16 no deslocamento de byte especificado desde o início do modo de exibição.|  
|[Método getInt32 (DataView)](../../javascript/reference/getint32-method-dataview.md)|Obtém o valor de Int32 no deslocamento de byte especificado desde o início do modo de exibição.|  
|[Método getUint32 (DataView)](../../javascript/reference/getuint32-method-dataview.md)|Obtém o valor Uint32 no deslocamento de byte especificado desde o início do modo de exibição.|  
|[Método getFloat32 (DataView)](../../javascript/reference/getfloat32-method-dataview.md)|Obtém o valor Float32 no deslocamento de byte especificado desde o início do modo de exibição.|  
|[Método getFloat64 (DataView)](../../javascript/reference/getfloat64-method-dataview.md)|Obtém o valor Float64 no deslocamento de byte especificado desde o início do modo de exibição.|  
|[Método setInt8 (DataView)](../../javascript/reference/setint8-method-dataview.md)|Armazena um valor Int8 no deslocamento de byte especificado desde o início do modo de exibição.|  
|[Método setUint8 (DataView)](../../javascript/reference/setuint8-method-dataview.md)|Armazena um valor Uint8 no deslocamento de byte especificado desde o início do modo de exibição.|  
|[Método setInt16 (DataView)](../../javascript/reference/setint16-method-dataview.md)|Armazena um valor Int16 no deslocamento de byte especificado desde o início do modo de exibição.|  
|[Método setUint16 (DataView)](../../javascript/reference/setuint16-method-dataview.md)|Armazena um valor Uint16 no deslocamento de byte especificado desde o início do modo de exibição.|  
|[Método setInt32 (DataView)](../../javascript/reference/setint32-method-dataview.md)|Armazena um valor Int32 no deslocamento de byte especificado desde o início do modo de exibição.|  
|[Método setUint32 (DataView)](../../javascript/reference/setuint32-method-dataview.md)|Armazena um valor Uint32 no deslocamento de byte especificado desde o início do modo de exibição.|  
|[Método setFloat32 (DataView)](../../javascript/reference/setfloat32-method-dataview.md)|Armazena um valor Float32 no deslocamento de byte especificado desde o início do modo de exibição.|  
|[Método setFloat64 (DataView)](../../javascript/reference/setfloat64-method-dataview.md)|Armazena um valor Float64 no deslocamento de byte especificado desde o início do modo de exibição.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar um objeto de DataView para processar os dados binários adquiridos de uma XmlHttpRequest:  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            var ints = new Int32Array(dataView.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]