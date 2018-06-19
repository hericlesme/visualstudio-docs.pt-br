---
title: Método Delete (WeakMap) (JavaScript) | Microsoft Docs
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
ms.assetid: 7d54ae55-e514-45ba-b403-d1eee46837d2
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd4cec06b77b7198e23d7e455849b5c0bf6d7ff9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636326"
---
# <a name="delete-method-weakmap-javascript"></a>Método delete (WeakMap) (JavaScript)
Remove o elemento especificado de um objeto `WeakMap`.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
weakmapObj.delete(key)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `weakmapObj`  
 Necessário. Um objeto `WeakMap`.  
  
 `key`  
 Necessário. A chave do elemento a ser removido.  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 `true` se o elemento tiver sido removido.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como adicionar um membro a um `WeakMap` e, em seguida, excluí-lo.  
  
```JavaScript  
function Dog(breed) {  
    this.breed = breed;  
}  
  
var dog = new Dog("yorkie");  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.delete(dog);  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]