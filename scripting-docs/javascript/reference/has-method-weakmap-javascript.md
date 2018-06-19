---
title: Método has (WeakMap) (JavaScript) | Microsoft Docs
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
ms.assetid: 12bedca1-bde7-413a-a4e2-06c03559044f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9a1706a1b96b5273ec280c4cef2be47a3bc6e17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636686"
---
# <a name="has-method-weakmap-javascript"></a>Método has (WeakMap) (JavaScript)
Retorna `true` se o `WeakMap` objeto contém o elemento especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
weakmapObj.has(key)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `weakmapObj`  
 Necessário. Um objeto `WeakMap`.  
  
 `key`  
 Necessário. A chave do elemento para teste.  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 `true`Se o `WeakMap` contém a chave especificada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como adicionar um membro a um `WeakMap` e, em seguida, usar `has` para verificar se ele está presente.  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
  
document.write(wm.has(dog));  
  
// Output:  
// true  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]