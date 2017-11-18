---
title: "Método Set (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: 29fc72b1-224f-4f19-8c06-5d926d695b03
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c916bda13c7bd973b37c4e4cb6b81e327ee5de54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="set-method-weakmap-javascript"></a>Método set (WeakMap) (JavaScript)
Adiciona um novo elemento a um `WeakMap` objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
weakmapObj.set(key, value)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `weakmapObj`  
 Necessário. Um objeto `WeakMap`.  
  
 `key`  
 Necessário. Um objeto que representa a chave do elemento a ser adicionado. Isso deve ser uma referência de objeto.  
  
 `value`  
 Necessário. O valor do elemento a ser adicionado.  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 Retorna o `WeakMap` objeto que contém o par chave/valor novo.  
  
## <a name="remarks"></a>Comentários  
 Se você adicionar um valor à coleção usando uma chave existente, o novo valor substituirá o valor antigo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como adicionar membros a um `WeakMap` objeto.  
  
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
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]