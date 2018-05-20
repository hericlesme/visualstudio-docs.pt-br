---
title: Método forEach (Map) (JavaScript) | Microsoft Docs
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
ms.assetid: 9cdf0adc-77c7-4407-8ba7-ada0fb09e507
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 549d7d625fb4dfe88b2db69e6aa0ff66c7e90f66
ms.sourcegitcommit: 37144589d9f850ff81ec7bfb884429989925a43d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2018
---
# <a name="foreach-method-map-javascript"></a>Método forEach (Map) (JavaScript)
Executa a ação especificada para cada elemento em um mapa.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
mapObj.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `mapObj`  
 Necessário. Um objeto `Map`.  
  
 `callbackfn`  
 Necessário. A função que `forEach` chama uma vez para cada elemento no mapa. `callbackfn` aceita até três argumentos. `forEach` chamadas de `callbackfn` função uma vez para cada elemento no mapa.  
  
 `thisArg`  
 Opcional. Um objeto que o `this` pode referir-se na palavra-chave de `callbackfn` função. Se `thisArg` for omitido, `undefined` será usado como o valor de `this`.  
  
## <a name="exceptions"></a>Exceções  
 Se o argumento `callbackfn` não for um objeto de função, uma exceção `TypeError` será acionada.  
  
## <a name="remarks"></a>Comentários  
 A sintaxe da função de retorno de chamada é a seguinte:  
  
 `function callbackfn(value, key, mapObj)`  
  
 Você pode declarar a função de retorno de chamada usando até três parâmetros, conforme mostrado na tabela a seguir.  
  
|Argumento de retorno de chamada|Definição|  
|-----------------------|----------------|  
|`value`|Um valor contido no mapa.|  
|`key`|Uma chave contida no mapa.|  
|`mapObj`|O `Map` objeto passem.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como recuperar membros de um `Map` usando `forEach`.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (value, key, mapObj) {  
    document.write(value.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]
