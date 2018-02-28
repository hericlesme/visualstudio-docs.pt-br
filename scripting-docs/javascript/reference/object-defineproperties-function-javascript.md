---
title: "Função Object defineproperties (JavaScript) | Microsoft Docs"
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
helpviewer_keywords:
- Object.defineProperties function [JavaScript]
ms.assetid: 2dae6658-a1c9-495f-bf06-bb3e964e6762
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 65f4f5817a105283a26c971bd98869d000ca0bc2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="objectdefineproperties-function-javascript"></a>Função Object.defineProperties (JavaScript)
Adiciona uma ou mais propriedades a um objeto e/ou modifica os atributos de propriedades existentes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
object.defineProperties(object, descriptors)  
```  
  
## <a name="parameters"></a>Parâmetros  
 `object`  
 Necessário. O objeto no qual adicionar ou modificar as propriedades. Isso pode ser um nativo [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objeto ou um objeto DOM.  
  
 `descriptors`  
 Necessário. Um [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objeto que contém um ou mais objetos do descritor. Cada objeto descritor descreve uma propriedade de dados ou uma propriedade do acessador.  
  
## <a name="return-value"></a>Valor de retorno  
 O objeto que foi passado para a função.  
  
## <a name="remarks"></a>Comentários  
 O `descriptors` argumento é um objeto que contém um ou mais objetos do descritor.  
  
 Um *propriedade dados* é uma propriedade que pode armazenar e recuperar um valor. Um descritor de propriedade de dados contém um `value` atributo, um `writable` atributo, ou ambos. Para obter mais informações, consulte [propriedades de dados e propriedades de acessador](../../javascript/advanced/data-properties-and-accessor-properties.md).  
  
 Um *propriedade do acessador* chama uma função fornecida pelo usuário sempre que o valor da propriedade é definido ou recuperado. Um descritor de propriedade do acessador contém um `set` atributo, um `get` atributo, ou ambos.  
  
 Se o objeto já tem uma propriedade que tem o nome especificado, os atributos de propriedade são modificados. Para obter mais informações, consulte [função Object defineproperty](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
 Para criar um objeto e adicionar propriedades ao novo objeto, você pode usar o [função Object](../../javascript/reference/object-create-function-javascript.md).  
  
## <a name="adding-properties"></a>Adicionando Propriedades  
 No exemplo a seguir, o `Object.defineProperties` função adiciona uma propriedade de dados e uma propriedade de acessador a um objeto definido pelo usuário.  
  
 O exemplo usa um literal de objeto para criar o `descriptors` do objeto com o `newDataProperty` e `newAccessorProperty` objetos do descritor.  
  
```JavaScript  
var newLine = "<br />";  
  
var obj = {};  
Object.defineProperties(obj, {  
    newDataProperty: {  
        value: 101,  
        writable: true,  
        enumerable: true,  
        configurable: true  
    },  
    newAccessorProperty: {  
        set: function (x) {  
            document.write("in property set accessor" + newLine);  
            this.newaccpropvalue = x;  
        },  
        get: function () {  
            document.write("in property get accessor" + newLine);  
            return this.newaccpropvalue;  
        },  
        enumerable: true,  
        configurable: true  
    }});  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
 Como o exemplo anterior, o exemplo a seguir adiciona propriedades dinamicamente em vez de com um literal de objeto.  
  
```JavaScript  
  
var newLine = "<br />";  
  
// Create the descriptors object.  
var descriptors = new Object();  
  
// Add a data property descriptor to the descriptors object.  
descriptors.newDataProperty = new Object();  
descriptors.newDataProperty.value = 101;  
descriptors.newDataProperty.writable = true;  
descriptors.newDataProperty.enumerable = true;  
descriptors.newDataProperty.configurable = true;  
  
// Add an accessor property descriptor to the descriptors object.  
descriptors.newAccessorProperty = new Object();  
descriptors.newAccessorProperty.set = function (x) {  
    document.write("in property set accessor" + newLine);  
    this.newaccpropvalue = x;  
};  
descriptors.newAccessorProperty.get = function () {  
    document.write("in property get accessor" + newLine);  
    return this.newaccpropvalue;  
};  
descriptors.newAccessorProperty.enumerable = true;  
descriptors.newAccessorProperty.configurable = true;  
  
// Call the Object.defineProperties function.  
var obj = new Object();  
Object.defineProperties(obj, descriptors);  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
## <a name="modifying-properties"></a>Modificando Propriedades  
 Para modificar os atributos de propriedade para o objeto, adicione o código a seguir. O `Object.defineProperties` função modifica o `writable` atributo de `newDataProperty`e modifica o `enumerable` atributo de `newAccessorProperty`. Ele adiciona `anotherDataProperty` ao objeto porque esse nome de propriedade já não existe.  
  
```  
Object.defineProperties(obj, {  
    newDataProperty: { writable: false },  
    newAccessorProperty: { enumerable: false },  
    anotherDataProperty: { value: "abc" }  
});  
```  
  
## <a name="requirements"></a>Requisitos  
 Com suporte nos padrões do Internet Explorer 9, padrões do Internet Explorer 10, e [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] aplicativos. Com suporte no Internet Explorer 8 para objetos de DOM, caso contrário, não tem suporte.  
  
## <a name="see-also"></a>Consulte também  
 [Função Object getownpropertydescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Função Object getownpropertynames](../../javascript/reference/object-getownpropertynames-function-javascript.md)   
 [Função Object defineproperty](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Função Object.](../../javascript/reference/object-create-function-javascript.md)   
 [Objeto Object](../../javascript/reference/object-object-javascript.md)