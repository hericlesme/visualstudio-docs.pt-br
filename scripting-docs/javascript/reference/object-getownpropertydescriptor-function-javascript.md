---
title: Função Object getownpropertydescriptor (JavaScript) | Microsoft Docs
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
- getOwnPropertyDescriptor method [JavaScript]
ms.assetid: 8f0e1c90-c4f9-44c4-bf76-726bacecbc14
caps.latest.revision: 45
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd147d567fc4d8a39d7a251d55772c40518e7a26
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639026"
---
# <a name="objectgetownpropertydescriptor-function-javascript"></a>Função Object.getOwnPropertyDescriptor (JavaScript)
Obtém o descritor de propriedade próprio do objeto especificado. Um descritor de propriedade próprio é aquele definido diretamente no objeto, e não herdado do protótipo do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Object.getOwnPropertyDescriptor(object, propertyname)  
```  
  
## <a name="parameters"></a>Parâmetros  
 `object`  
 Necessário. O objeto que contém a propriedade.  
  
 `propertyname`  
 Necessário. O nome da propriedade.  
  
## <a name="return-value"></a>Valor de retorno  
 O descritor da propriedade.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar a função `Object.getOwnPropertyDescriptor` para obter um objeto descritor que descreve os atributos da propriedade.  
  
 O [função Object defineproperty](../../javascript/reference/object-defineproperty-function-javascript.md) é usado para adicionar ou modificar propriedades.  
  
## <a name="data-property-example"></a>Exemplo da Propriedade de Dados  
 O exemplo a seguir obtém um descritor de propriedade de dados e o utiliza para tornar a propriedade somente leitura.  
  
```JavaScript  
// Create a user-defined object.  
var obj = {};  
  
// Add a data property.  
obj.newDataProperty = "abc";  
  
// Get the property descriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// Change a property attribute.  
descriptor.writable = false;  
Object.defineProperty(obj, "newDataProperty", descriptor);  
  
```  
  
 Para listar atributos da propriedade, adicione o seguinte código a este exemplo.  
  
```JavaScript  
// Get the descriptor from the object.  
var desc2 = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// List the descriptor attributes.  
for (var prop in desc2) {  
    document.write(prop + ': ' + desc2[prop]);  
    document.write("<br />");  
}  
  
// Output:  
// value: abc  
// writable: false  
// enumerable: true  
// configurable: true  
```  
  
## <a name="requirements"></a>Requisitos  
 Há suporte para todos os recursos no [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)].  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] dá suporte a objetos DOM, mas não a objetos definidos pelo usuário. Os atributos `enumerable` e `configurable` podem ser especificados, mas não são usados.  
  
## <a name="see-also"></a>Consulte também  
 [Protótipos de modelo de objeto de documento, parte 2: Acessador (getter/setter) suporte](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Função Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)