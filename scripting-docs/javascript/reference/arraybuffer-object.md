---
title: Objeto ArrayBuffer | Microsoft Docs
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
ms.assetid: 9fda1261-f450-493b-b3db-ecfa9ca93cd7
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c253d63d12a4a5e71d1661aae560b74debecdd62
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634316"
---
# <a name="arraybuffer-object"></a>Objeto ArrayBuffer
Representa um buffer bruto de dados binários, usado para armazenar dados para as diferentes matrizes digitadas. `ArrayBuffers`não é possível ler ou gravar diretamente, mas pode ser passado para uma matriz tipada ou [objeto DataView](../../javascript/reference/dataview-object.md) para interpretar o buffer bruto conforme necessário.  
  
 Para obter mais informações sobre matrizes de tipo, consulte [matrizes tipadas](../../javascript/advanced/typed-arrays-javascript.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
  
arrayBuffer = new ArrayBuffer(length);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `arrayBuffer`  
 Obrigatório. O nome da variável à qual o objeto `ArrayBuffer` é atribuído.  
  
 `length`  
 O comprimento do buffer. O conteúdo de ArrayBuffer é iniciado em 0. Se o número de bytes solicitado não puder ser alocado, uma exceção será gerada.  
  
## <a name="properties"></a>Propriedades  
 A tabela a seguir lista as propriedades do objeto `ArrayBuffer`.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|[Propriedade byteLength](../../javascript/reference/bytelength-property-arraybuffer.md)|Somente leitura. O comprimento de ArrayBuffer (em bytes).|  
  
## <a name="functions"></a>Funções  
 A tabela a seguir lista as funções do objeto `ArrayBuffer`.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|[Função Isview](../../javascript/reference/arraybuffer-isview-function-arraybuffer.md)|Determina se um objeto fornece uma visão do buffer.|  
  
## <a name="methods"></a>Métodos  
 A tabela a seguir lista os métodos do objeto `ArrayBuffer`.  
  
|Propriedade|Descrição|  
|--------------|-----------------|  
|[Método slice](../../javascript/reference/slice-method-arraybuffer.md)|Retorna uma seção de um `ArrayBuffer`.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar um objeto ArrayBuffer para processar os dados binários adquiridos de uma [XMLHttpRequest](http://msdn.microsoft.com/library/ie/ms535874\(v=vs.85\).aspx). Você pode usar um [objeto DataView](../../javascript/reference/dataview-object.md) para obter os valores individuais.  
  
```JavaScript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataview = new DataView(buffer);  
            var ints = new Int32Array(buffer.byteLength / 4);  
            for (var i = 0; i < ints.length; i++) {  
                ints[i] = dataview.getInt32(i * 4);  
            }  
        alert(ints[10]);  
        }  
    }  
  
```  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre como usar `XmlHttpRequest`, consulte [aprimoramentos de XMLHttpRequest](http://msdn.microsoft.com/en-us/be09137c-6546-441b-b953-dcbf72b77069).  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]