---
title: Método Get (WeakMap) (JavaScript) | Microsoft Docs
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
ms.assetid: d922c55d-486d-4feb-aedc-1f4867c417d2
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29decb7e6a050188b75639eb7cf4f27494b31da2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636486"
---
# <a name="get-method-weakmap-javascript"></a>Método get (WeakMap) (JavaScript)
Retorna um elemento especificado de uma `WeakMap` objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
weakmapObj.get(key)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `weakmapObj`  
 Necessário. Um objeto `WeakMap`.  
  
 `key`  
 Necessário. A chave de um elemento de `WeakMap`.  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 Retorna o objeto associado à chave. Se o `WeakMap` não contém a chave, este método retorna um `undefined` valor.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como recuperar membros de uma `WeakMap` objeto.  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]