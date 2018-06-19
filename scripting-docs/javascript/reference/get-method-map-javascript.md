---
title: Método Get (Map) (JavaScript) | Microsoft Docs
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
ms.assetid: bebbd6bc-6e61-4674-8196-7e907798973f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 243d5aa93289cb7a13b34567b7824d028151bad3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636446"
---
# <a name="get-method-map-javascript"></a>Método get (Map) (JavaScript)
Retorna um elemento especificado de um mapa.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
mapObj.get(key)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `mapObj`  
 Necessário. Um objeto `Map`.  
  
 `key`  
 Necessário. A chave de um elemento de `Map`.  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 Retorna o objeto associado à chave. Se o `Map` não contém a chave, este método retorna um `undefined` valor.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como recuperar um elemento de uma `Map` objeto.  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
document.write(m.get(2));  
  
// Output:  
// red  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]