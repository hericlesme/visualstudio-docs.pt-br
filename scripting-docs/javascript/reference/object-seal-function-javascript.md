---
title: Função Object seal (JavaScript) | Microsoft Docs
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
- Object.seal function
- seal function
ms.assetid: e72c804a-4dab-4ec9-b9df-9c9c908aa12d
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dca9066be9a557b97a52ae749cecfb218504509
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641146"
---
# <a name="objectseal-function-javascript"></a>Função Object.seal (JavaScript)
Impede a modificação de atributos de propriedades existentes e impede a adição de novas propriedades.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
Object.seal(object)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `object`  
 Necessário. O objeto no qual os atributos de bloqueio.  
  
## <a name="return-value"></a>Valor de retorno  
 O objeto que é passado para a função.  
  
## <a name="exceptions"></a>Exceções  
 Se o `object` argumento não é um objeto, um `TypeError` exceção será lançada.  
  
## <a name="remarks"></a>Comentários  
 O `Object.seal` função faz o seguinte:  
  
-   Torna o objeto não-extensível, para que as novas propriedades não podem ser adicionadas a ele.  
  
-   Conjuntos de `configurable` atributo `false` para todas as propriedades do objeto.  
  
 Quando o `configurable` atributo é `false`, atributos de propriedade não podem ser alterados e a propriedade não pode ser excluída. Quando `configurable` é `false` e `writable` é `true`, o `value` e `writable` atributos podem ser alterados.  
  
 O `Object.seal` função não altera o `writable` atributo.  
  
 Para obter mais informações sobre como definir atributos de propriedade, consulte [função Object defineproperty](../../javascript/reference/object-defineproperty-function-javascript.md). Para obter os atributos de uma propriedade, você pode usar o [função Object getownpropertydescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="related-functions"></a>Funções relacionadas  
 As seguintes funções relacionadas impedir a modificação de atributos de objeto.  
  
|Função|Objeto é feito não extensível|`configurable`é definido como `false` para cada propriedade|`writable`é definido como `false` para cada propriedade|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Preventextensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Sim|Não|Não|  
|`Object.seal`|Sim|Sim|Não|  
|[Freeze](../../javascript/reference/object-freeze-function-javascript.md)|Sim|Sim|Sim|  
  
 Os seguintes funções retornam `true` se todas as condições marcadas na tabela a seguir forem verdadeiras.  
  
|Função|Objeto é extensível?|`configurable`é `false` para todas as propriedades?|`writable`é `false` para todas as propriedades de dados?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Isextensible](../../javascript/reference/object-isextensible-function-javascript.md)|Sim|Não|Não|  
|[IsSealed](../../javascript/reference/object-issealed-function-javascript.md)|Não|Sim|Não|  
|[IsFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Não|Sim|Sim|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da função `Object.seal`.  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
// Seal the object.  
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
 [Função Object Freeze](../../javascript/reference/object-freeze-function-javascript.md)   
 [Função Object isextensible](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Função Object IsSealed](../../javascript/reference/object-issealed-function-javascript.md)   
 [Função Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)