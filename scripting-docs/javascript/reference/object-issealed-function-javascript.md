---
title: "Função Object IsSealed (JavaScript) | Microsoft Docs"
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
- properties [JavaScript], locking attributes
- isSealed function [JavaScript]
- Object.isSealed [JavaScript]
ms.assetid: af4f192e-cebe-44b9-8eef-90c096f5ae8f
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d3b9cb603a456382e3b23e6f7d0037063027b98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="objectissealed-function-javascript"></a>Função Object.isSealed (JavaScript)
Retorna `true` se atributos da propriedade existente não puderem ser modificados em um objeto e novas propriedades não puderem ser adicionadas ao objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
Object.isSealed(object)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `object`  
 Necessário. O objeto a ser testado.  
  
## <a name="return-value"></a>Valor de retorno  
 `true`Se as seguintes são verdadeiras:  
  
-   O objeto é não-extensível, que indica que as novas propriedades não podem ser adicionadas ao objeto.  
  
-   O `configurable` atributo é `false` para todas as propriedades existentes.  
  
 Se o objeto não tem todas as propriedades, a função retorna `true` se o objeto é não-extensível.  
  
## <a name="exceptions"></a>Exceções  
 Se o `object` argumento não é um objeto, um `TypeError` exceção será lançada.  
  
## <a name="remarks"></a>Comentários  
 Quando o `configurable` atributo de uma propriedade é `false`, os atributos de propriedade não podem ser alterados e a propriedade não pode ser excluída. Quando `writable` é `false`, o valor da propriedade de dados não pode ser alterado. Quando `configurable` é `false` e `writable` é `true`, o `value` e `writable` atributos podem ser alterados.  
  
 O `Object.isSealed` função não usa o `writable` atributo de propriedades para determinar o valor de retorno.  
  
 Para obter informações sobre como definir atributos de propriedade, consulte [função Object defineproperty](../../javascript/reference/object-defineproperty-function-javascript.md). Para obter os atributos de uma propriedade, você pode usar o [função Object getownpropertydescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="related-functions"></a>Funções relacionadas  
 As seguintes funções relacionadas impedir a modificação de atributos de objeto.  
  
|Função|Objeto é feito não extensível|`configurable`é definido como `false` para cada propriedade|`writable`é definido como `false` para cada propriedade|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Preventextensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Sim|Não|Não|  
|[Seal](../../javascript/reference/object-seal-function-javascript.md)|Sim|Sim|Não|  
|[Freeze](../../javascript/reference/object-freeze-function-javascript.md)|Sim|Sim|Sim|  
  
 Os seguintes funções retornam `true` se todas as condições marcadas na tabela a seguir forem verdadeiras.  
  
|Função|Objeto é extensível?|`configurable`é `false` para todas as propriedades?|`writable`é `false` para todas as propriedades de dados?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Isextensible](../../javascript/reference/object-isextensible-function-javascript.md)|Sim|Não|Não|  
|`Object.isSealed`|Não|Sim|Não|  
|[IsFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Não|Sim|Sim|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da função `Object.isSealed`.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Seal the object, and verify that it is sealed.  
Object.seal(obj);  
document.write(Object.isSealed(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write(obj.newProp);  
document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
  
// Output:  
// true  
// undefined  
// 10  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função Object preventextensions](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Função Object seal](../../javascript/reference/object-seal-function-javascript.md)   
 [Função Object Freeze](../../javascript/reference/object-freeze-function-javascript.md)   
 [Função Object isextensible](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Função Object IsFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)   
 [Função Object defineproperty](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Função Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)