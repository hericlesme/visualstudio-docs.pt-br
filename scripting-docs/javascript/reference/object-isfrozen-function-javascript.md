---
title: Função Object IsFrozen (JavaScript) | Microsoft Docs
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
helpviewer_keywords:
- isFrozen function [JavaScript]
- Object.isFrozen function [JavaScript]
ms.assetid: 6cf1bbc6-56e8-429b-8e2c-0024fa614acc
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e1ccd11d5b4ef3b5f24dbfc8e815f0e3e156347
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641706"
---
# <a name="objectisfrozen-function-javascript"></a>Função Object.isFrozen (JavaScript)
Retorna `true` se os valores e os atributos da propriedade existente não podem ser modificados em um objeto e novas propriedades não podem ser adicionadas ao objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
Object.isFrozen(object)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `object`  
 Necessário. O objeto a ser testado.  
  
## <a name="return-value"></a>Valor de retorno  
 `true`Se todos os itens a seguir forem verdadeiras:  
  
-   O objeto é não-extensível, que indica que as novas propriedades não podem ser adicionadas ao objeto.  
  
-   O `configurable` atributo é `false` para todas as propriedades existentes.  
  
-   O `writable` atributo é `false` para todas as propriedades de dados existente.  
  
 Se o objeto não tiver nenhuma propriedade existente, a função retorna `true` se o objeto é não-extensível.  
  
## <a name="exceptions"></a>Exceções  
 Se o `object` argumento não é um objeto, um `TypeError` exceção será lançada.  
  
## <a name="remarks"></a>Comentários  
 Quando o `configurable` atributo de uma propriedade é `false`, os atributos de propriedade não podem ser alterados e a propriedade não pode ser excluída. Quando `writable` é `false`, o valor da propriedade de dados não pode ser alterado. Quando `configurable` é `false` e `writable` é `true`, o `value` e `writable` atributos podem ser alterados.  
  
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
|[IsSealed](../../javascript/reference/object-issealed-function-javascript.md)|Não|Sim|Não|  
|`Object.isFrozen`|Não|Sim|Sim|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da função `Object.isFrozen`.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object, and verify that it is frozen.  
Object.freeze(obj);  
document.write(obj.isFrozen());  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write (obj.newProp);  
document.write ("<br/>");  
  
// Try to delete a property, and then verify that it is still present.  
delete obj.length;  
document.write (obj.length);  
document.write ("<br/> ");  
  
// Try to change a property value, and then verify that it is not changed.  
obj.pasta = "linguini";  
document.write (obj.pasta);  
  
// Output:  
// true  
// undefined  
// 10  
// spaghetti  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função Object preventextensions](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Função Object seal](../../javascript/reference/object-seal-function-javascript.md)   
 [Função Object Freeze](../../javascript/reference/object-freeze-function-javascript.md)   
 [Função Object isextensible](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Função Object IsSealed](../../javascript/reference/object-issealed-function-javascript.md)   
 [Função Object defineproperty](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Função Object getownpropertydescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Função Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)