---
title: O objeto de proxy (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2b89abee-04fa-47e6-9676-980016cff5f8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ee75310f1d976e0a0896b1be34a80c594cdd054
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="proxy-object-javascript"></a>Objeto Proxy (JavaScript)
Habilita um comportamento personalizado para um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
proxyObj = new Proxy(target, handler)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `target`  
 Necessário. Um objeto ou uma função a ser virtualizado pelo proxy.  
  
 `handler`  
 Necessário. Um objeto com métodos (interceptações) que implementam o comportamento personalizado.  
  
## <a name="remarks"></a>Comentários  
 Um objeto `Proxy` é usado para interceptar operações internas de nível baixo em outro objeto. Objetos de proxy podem ser usados para interceptação, virtualização de objeto, registro em log/criação de perfil e outras finalidades.  
  
 Se uma interceptação para uma operação específica não tiver sido definida no manipulador para o proxy, a operação será encaminhada para o destino.  
  
 O objeto do manipulador define os seguintes métodos (interceptações) para implementar o comportamento personalizado. Estes exemplos não são exaustivos. Para dar suporte a comportamento condicional padrão no método do manipulador, use métodos de [refletir objeto](../../javascript/reference/reflect-object-javascript.md).  
  
|Sintaxe (interceptação) do método do manipulador|Exemplos de uso|  
|------------------------------------|-----------------------|  
|`apply: function(target, thisArg, args)`|Uma interceptação para uma chamada de função.|  
|`construct: function(target, args)`|Uma interceptação para um construtor.|  
|`defineProperty: function(target, propertyName, descriptor)`|Uma interceptação para [função Object defineproperty](../../javascript/reference/object-defineproperty-function-javascript.md).|  
|`deleteProperty: function(target, propertyName)`|Uma interceptação para a instrução `delete`.|  
|`enumerate: function(target)`|Uma interceptação para a [loop for... no](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) instrução, [Object. getownpropertysymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md), [Keys](../../javascript/reference/object-keys-function-javascript.md) função, e [stringify](../../javascript/reference/json-stringify-function-javascript.md).|  
|`get: function(target, propertyName, receiver)`|Uma interceptação para quaisquer [getter](../../javascript/creating-objects-javascript.md) propriedades.|  
|`getOwnPropertyDescriptor: function(target, propertyName)`|Uma interceptação para [função Object getownpropertydescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).|  
|`getPrototypeOf: function(target)`|Uma interceptação para [função Object. getprototypeof](../../javascript/reference/object-getprototypeof-function-javascript.md).|  
|`has: function(target, propertyName)`|Uma interceptação para a `in` operador, [método hasOwnProperty (Object)](../../javascript/reference/hasownproperty-method-object-javascript.md)e outros métodos.|  
|`isExtensible: function(target)`|Uma interceptação para [função Object isextensible](../../javascript/reference/object-isextensible-function-javascript.md).|  
|`ownKeys: function(target)`|Uma interceptação para [função Object getownpropertynames](../../javascript/reference/object-getownpropertynames-function-javascript.md).|  
|`preventExtensions: function(target)`|Uma interceptação para [função Object preventextensions](../../javascript/reference/object-preventextensions-function-javascript.md).|  
|`set: function(target, propertyName, value, receiver)`|Uma interceptação para quaisquer [setter](../../javascript/creating-objects-javascript.md) propriedades.|  
|`setPrototypeOf: function(target, prototype)`|Uma interceptação para [setprototypeof](../../javascript/reference/object-setprototypeof-function-javascript.md).|  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como criar um proxy para um literal de objeto usando a interceptação `get`.  
  
```JavaScript  
var target = {};  
var handler = {  
  get: function (target, property, receiver) {  
    // This example includes a template string.  
    return `Hello, ${property}!`;  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(p.world);  
  
// Output:  
// Hello, world!  
  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como criar um proxy para uma função usando a interceptação `apply`.  
  
```JavaScript  
var target = function () { return 'I am the target'; };  
var handler = {  
  // This example includes a rest parameter.  
  apply: function (receiver, ...args) {  
    return 'I am the proxy';  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(target()):  
console.log(p()):  
  
// Output:  
// I am the target  
// I am the proxy  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
