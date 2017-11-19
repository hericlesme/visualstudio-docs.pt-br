---
title: "Função Object preventextensions (JavaScript) | Microsoft Docs"
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
helpviewer_keywords:
- properties [JavaScript], preventing new
- preventing new properties [JavaScript]
- preventExtensions function [JavaScript]
- Object.preventExtensions function [JavaScript]
ms.assetid: e6b48197-2374-4437-a9fe-519dd45a2077
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 868f917cc2249a1634194e4b2dd097e0dcbd4c08
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="objectpreventextensions-function-javascript"></a>Função Object.preventExtensions (JavaScript)
Impede a adição de novas propriedades a um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
Object.preventExtensions(object)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `object`  
 Necessário. O objeto a tornar não extensível.  
  
## <a name="return-value"></a>Valor de retorno  
 O objeto que é passado para a função.  
  
## <a name="exceptions"></a>Exceções  
 Se o `object` argumento não é um objeto, um `TypeError` exceção será lançada.  
  
## <a name="remarks"></a>Comentários  
 O `Object.preventExtensions` função faz com que um objeto não-extensível, para que as novas propriedades nomeadas não podem ser adicionadas a ele. Depois que um objeto é feito não extensível, ele não pode se tornar extensível.  
  
 Para obter informações sobre como definir atributos de propriedade, consulte [função Object defineproperty](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## <a name="related-functions"></a>Funções relacionadas  
 As seguintes funções relacionadas impedir a modificação de atributos de objeto.  
  
|Função|Objeto é feito não extensível|`configurable`é definido como `false` para cada propriedade|`writable`é definido como `false` para cada propriedade|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|`Object.preventExtensions`|Sim|Não|Não|  
|[Seal](../../javascript/reference/object-seal-function-javascript.md)|Sim|Sim|Não|  
|[Freeze](../../javascript/reference/object-freeze-function-javascript.md)|Sim|Sim|Sim|  
  
 Os seguintes funções retornam `true` se todas as condições marcadas na tabela a seguir forem verdadeiras.  
  
|Função|Objeto é extensível?|`configurable`é `false` para todas as propriedades?|`writable`é `false` para todas as propriedades de dados?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Isextensible](../../javascript/reference/object-isextensible-function-javascript.md)|Sim|Não|Não|  
|[IsSealed](../../javascript/reference/object-issealed-function-javascript.md)|Não|Sim|Não|  
|[IsFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Não|Sim|Sim|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da função `Object.preventExtensions`.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
document.write(Object.isExtensible(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
// false  
// undefined  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função Object seal](../../javascript/reference/object-seal-function-javascript.md)   
 [Função Object Freeze](../../javascript/reference/object-freeze-function-javascript.md)   
 [Função Object isextensible](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Função Object IsSealed](../../javascript/reference/object-issealed-function-javascript.md)   
 [Função Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)