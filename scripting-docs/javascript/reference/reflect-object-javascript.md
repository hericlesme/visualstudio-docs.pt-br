---
title: Objeto reflect (JavaScript) | Microsoft Docs
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
ms.assetid: 1df74f34-2eb4-42f1-a930-b943c86daa0e
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3574c54ee7ff69f56951cd7f4c9a93cac5275fc1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="reflect-object-javascript"></a>Objeto Reflect (JavaScript)
Fornece métodos para uso em operações que são interceptadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Reflect.[method]  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `method`  
 Obrigatório. Nome de um dos métodos do objeto `Reflect`.  
  
## <a name="remarks"></a>Comentários  
 O objeto Reflect não pode ser instanciado com o operador `new`.  
  
 Reflexão métodos geralmente são usados com [proxies](../../javascript/reference/proxy-object-javascript.md) porque elas permitem que você delegue o comportamento padrão sem implementar o comportamento padrão em seu código.  
  
 A reflexão fornece um método estático com o mesmo nome de cada interceptação de proxy. As descrições da tabela não são exaustivas.  
  
|Método|Descrição|  
|------------|-----------------|  
|`Reflect.apply(target, thisArg, args)`|Como o [aplicar](../../javascript/reference/apply-method-function-javascript.md) método do objeto de função.|  
|`Reflect.construct(target, args)`|Uma função equivalente para o operador `new`.|  
|`Reflect.defineProperty(target, propertyName, descriptor)`|Semelhante ao [defineproperty](../../javascript/reference/object-defineproperty-function-javascript.md). Retorna um valor booliano que indica se a chamada foi bem-sucedida.|  
|`Reflect.deleteProperty(target, propertyName)`|Semelhante à instrução `delete`. Retorna um valor booliano que indica se a chamada foi bem-sucedida.|  
|`Reflect.enumerate(target)`|Semelhante ao [loop for... no](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) instrução, [Object. getownpropertysymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md), [Keys](../../javascript/reference/object-keys-function-javascript.md) função, e [stringify](../../javascript/reference/json-stringify-function-javascript.md).|  
|`Reflect.get(target, propertyName, receiver)`|Uma função equivalente para qualquer [getter](../../javascript/creating-objects-javascript.md) propriedades.|  
|`Reflect.getOwnPropertyDescriptor(target, propertyName)`|Semelhante ao [getownpropertydescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md). Retorna um valor booliano que indica se a chamada foi bem-sucedida.|  
|`Reflect.getPrototypeOf(target)`|Semelhante ao [getprototypeof](../../javascript/reference/object-getprototypeof-function-javascript.md).|  
|`Reflect.has(target, propertyName)`|Como o `in` operador, [método hasOwnProperty (Object)](../../javascript/reference/hasownproperty-method-object-javascript.md)e outros métodos. Retorna um valor booliano que indica se a chamada foi bem-sucedida.|  
|`Reflect.isExtensible(target)`|Semelhante ao [isextensible](../../javascript/reference/object-isextensible-function-javascript.md).|  
|`Reflect.ownKeys(target)`|Semelhante ao [getownpropertynames](../../javascript/reference/object-getownpropertynames-function-javascript.md).|  
|`Reflect.preventExtensions(target)`|Semelhante ao [preventextensions](../../javascript/reference/object-preventextensions-function-javascript.md). Retorna um valor booliano que indica se a chamada foi bem-sucedida.|  
|`Reflect.set(target, propertyName, value, receiver)`|Semelhante ao uso de qualquer [setter](../../javascript/creating-objects-javascript.md) propriedade. Retorna um valor booliano que indica se a chamada foi bem-sucedida.|  
|`Reflect.setPrototypeOf(target, prototype)`|Semelhante ao [setprototypeof](../../javascript/reference/object-setprototypeof-function-javascript.md). Retorna um valor booliano que indica se a chamada foi bem-sucedida.|  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como usar `Reflect.get` para escrever um proxy que bloqueia operações de obtenção para propriedades que começam com um sublinhado.  
  
```JavaScript  
var p = new Proxy({}, {  
    get(k, t, r) {  
        // return undefined if key begins with underscore  
        if(k[0] === '_') return undefined;  
  
       // otherwise do default behavior  
       return Reflect.get(k, t, r);  
    }  
});  
  
p._foo = 1;  
console.log(p._foo);  
  
p.foo = 1;  
console.log(p.foo);  
  
// Output:  
// undefined  
// 1  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]