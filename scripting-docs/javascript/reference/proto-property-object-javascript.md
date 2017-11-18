---
title: propriedade __proto__ (Object) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: __proto__
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 97c3f84d-125e-4905-b921-b021264964ee
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e38669c400acba6f4ed3c4ee3fb5836c31b1bc00
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="proto-property-object-javascript"></a>__proto__ propriedade (Object) (JavaScript)
Contém uma referência ao protótipo interno do objeto especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
object.__proto__  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `object`  
 Necessário. O objeto no qual definir o protótipo.  
  
## <a name="remarks"></a>Comentários  
 O `__proto__` propriedade pode ser usada para definir o protótipo de um objeto.  
  
 O objeto ou função herda todos os métodos e propriedades do novo protótipo, juntamente com todos os métodos e propriedades em cadeia de protótipos do novo protótipo. Um objeto pode ter apenas um único protótipo (não incluindo protótipos herdados na cadeia de protótipo), então quando você chama o `__proto__` propriedade, substitua o protótipo anterior.  
  
 Você pode definir o protótipo somente em um objeto extensível. Para obter mais informações, consulte [função Object preventextensions](../../javascript/reference/object-preventextensions-function-javascript.md).  
  
> [!NOTE]
>  O `__proto__` nome da propriedade começa e termina com dois sublinhados.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como definir o protótipo para um objeto.  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns true  
    rec.__proto__ = Object.prototype;  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns false  
}  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como adicionar propriedades a um objeto adicionando-os ao protótipo.  
  
```JavaScript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
obj.__proto__ = proto;  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir adiciona propriedades ao objeto `String`, definindo um novo protótipo nele.  
  
```JavaScript  
var stringProp = { desc: "description" };  
  
String.__proto__ = stringProp;  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    s1.__proto__ = String;  // Can't be set.  
    s2.__proto__ = String;  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Protótipos e herança de protótipos](../../javascript/advanced/prototypes-and-prototype-inheritance.md)