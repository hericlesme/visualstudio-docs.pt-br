---
title: "Função Object defineproperty (JavaScript) | Microsoft Docs"
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
- defineProperty function [JavaScript]
- Object.defineProperty function [JavaScript]
ms.assetid: c5d05346-940a-40c2-b12a-e8b25abc8d46
caps.latest.revision: "74"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89291f5c836f74a5dd71099328ce389a12f6fd24
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="objectdefineproperty-function-javascript"></a>Função Object.defineProperty (JavaScript)
Adiciona uma propriedade a um objeto ou modifica atributos de uma propriedade existente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Object.defineProperty(object, propertyname, descriptor)  
```  
  
## <a name="parameters"></a>Parâmetros  
 `object`  
 Necessário. O objeto ao qual adicionar ou no qual modificar a propriedade. Pode ser um objeto [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] nativo (ou seja, um objeto definido pelo usuário ou um objeto interno) ou um objeto DOM.  
  
 `propertyname`  
 Necessário. Uma cadeia de caracteres que contém o nome da propriedade.  
  
 `descriptor`  
 Necessário. Um descritor da propriedade. Pode ser uma propriedade de dados ou uma propriedade do acessador.  
  
## <a name="return-value"></a>Valor de retorno  
 O objeto modificado.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar a função `Object.defineProperty` para fazer o seguinte:  
  
-   Adicionar uma nova propriedade a um objeto. Isso ocorre quando o objeto não tem o nome da propriedade especificado.  
  
-   Modificar atributos de uma propriedade existente. Isso ocorre quando o objeto já tem o nome da propriedade especificado.  
  
 A definição da propriedade é fornecida em um objeto descritor, que descreve os atributos de uma propriedade de dados ou uma propriedade do acessador. O objeto descritor é um parâmetro da função `Object.defineProperty`.  
  
 Para adicionar várias propriedades para um objeto ou modificar várias propriedades existentes, você pode usar o [função Object defineproperties](../../javascript/reference/object-defineproperties-function-javascript.md).  
  
## <a name="exceptions"></a>Exceções  
 Um exceção `TypeError` será gerada se qualquer uma das seguintes condições for verdadeira:  
  
-   O argumento `object` não é um objeto.  
  
-   O objeto não é [extensível](../../javascript/reference/object-isextensible-function-javascript.md) e o nome da propriedade especificada não existe.  
  
-   O `descriptor` tem um atributo `value` ou `writable` e tem um atributo `get` ou `set`.  
  
-   O `descriptor` tem um atributo `get` ou `set` que não é uma função ou indefinido.  
  
-   O nome da propriedade especificado já existe, a propriedade existente tem um atributo `configurable` de `false` e o `descriptor` contém um ou mais atributos que são diferentes daqueles da propriedade existente. No entanto, quando a propriedade existente tem um atributo `configurable` de `false` e um atributo `writable` de `true`, é permitido que o atributo `value` ou `writable` seja diferente.  
  
## <a name="adding-a-data-property"></a>Adicionando uma Propriedade de Dados  
 No exemplo a seguir, a função `Object.defineProperty` adiciona uma propriedade de dados a um objeto definido pelo usuário. Para adicionar a propriedade a um objeto DOM existente, remova o comentário da linha `var = window.document`.  
  
```JavaScript  
var newLine = "<br />";  
  
// Create a user-defined object.  
var obj = {};  
  
// Add a data property to the object.  
Object.defineProperty(obj, "newDataProperty", {  
    value: 101,  
    writable: true,  
    enumerable: true,  
    configurable: true  
});  
  
// Set the property value.  
obj.newDataProperty = 102;  
document.write("Property value: " + obj.newDataProperty + newLine);  
  
// Output:  
// Property value: 102  
```  
  
 Para listar as propriedades do objeto, adicione o seguinte código a este exemplo.  
  
```JavaScript  
var names = Object.getOwnPropertyNames(obj);  
for (var i = 0; i < names.length; i++) {  
    var prop = names[i];  
  
    document.write(prop + ': ' + obj[prop]);  
    document.write(newLine);  
}  
  
// Output:  
//  newDataProperty: 102  
```  
  
## <a name="modifying-a-data-property"></a>Modificando uma Propriedade de Dados  
 Para modificar um atributo de propriedade do objeto, adicione o seguinte código à função `addDataProperty` mostrada anteriormente. O parâmetro `descriptor` contém apenas um atributo `writable`. Os outros atributos de propriedade de dados permanecem os mesmos.  
  
```JavaScript  
// Modify the writable attribute of the property.  
Object.defineProperty(obj, "newDataProperty", { writable: false });  
  
// List the property attributes by using a descriptor.  
// Get the descriptor with Object.getOwnPropertyDescriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
for (var prop in descriptor) {  
    document.write(prop + ': ' + descriptor[prop]);  
    document.write(newLine);  
}  
  
// Output  
// writable: false  
// value: 102  
// configurable: true  
// enumerable: true  
```  
  
## <a name="adding-an-accessor-property"></a>Adicionando uma Propriedade do Acessador  
 No exemplo a seguir, a função `Object.defineProperty` adiciona uma propriedade de acessador a um objeto definido pelo usuário.  
  
```JavaScript  
var newLine = "<br />";  
  
// Create a user-defined object.  
var obj = {};  
  
// Add an accessor property to the object.  
Object.defineProperty(obj, "newAccessorProperty", {  
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
});  
  
// Set the property value.  
obj.newAccessorProperty = 30;  
document.write("Property value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// Property value: 30  
  
```  
  
 Para listar as propriedades do objeto, adicione o seguinte código a este exemplo.  
  
```JavaScript  
var names = Object.getOwnPropertyNames(obj);  
for (var i = 0; i < names.length; i++) {  
    var prop = names[i];  
  
    document.write(prop + ': ' + obj[prop]);  
    document.write(newLine);  
}  
// Output:  
// in property get accessor  
// newAccessorProperty: 30  
  
```  
  
## <a name="modifying-an-accessor-property"></a>Modificando uma Propriedade do Acessador  
 Para modificar um atributo de propriedade do objeto, adicione o seguinte código ao código mostrado anteriormente. O parâmetro `descriptor` contém apenas uma definição de acessador `get`. Os outros atributos de propriedade permanecem os mesmos.  
  
```JavaScript  
// Modify the get accessor.  
Object.defineProperty(obj, "newAccessorProperty", {  
    get: function () { return this.newaccpropvalue; }  
});  
  
// List the property attributes by using a descriptor.  
// Get the descriptor with Object.getOwnPropertyDescriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newAccessorProperty");  
for (var prop in descriptor) {  
    document.write(prop + ': ' + descriptor[prop]);  
    document.write(newLine);  
}  
  
// Output:  
// get: function () { return this.newaccpropvalue; }  
// set: function (x) { document.write("in property set accessor" + newLine); this.newaccpropvalue = x; }  
// configurable: true  
// enumerable: true  
```  
  
## <a name="modifying-a-property-on-a-dom-element"></a>Modificando uma Propriedade em um Elemento DOM  
 O exemplo a seguir demonstra como personalizar propriedades DOM internas usando a função `Object.getOwnPropertyDescriptor` para obter e modificar o descritor de propriedade da propriedade. Para este exemplo, deve haver um elemento DIV com uma ID "div".  
  
```JavaScript  
// Get the querySelector property descriptor.  
var descriptor = Object.getOwnPropertyDescriptor(Element.prototype, "querySelector");  
  
// Make the property read-only.  
descriptor.value = "query";  
descriptor.writable = false;  
// Apply the changes to the Element prototype.  
Object.defineProperty(Element.prototype, "querySelector", descriptor);  
  
// Get a DOM element from the HTML body.  
var elem = document.getElementById("div");  
  
// Attempt to change the value. This causes the revised value attribute to be called.  
elem.querySelector = "anotherQuery";  
document.write(elem.querySelector);  
  
// Output:  
// query  
  
```  
  
## <a name="requirements"></a>Requisitos  
 Os modos padrão do Internet Explorer 9 e do Internet Explorer 10, bem como os aplicativos [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], dão suporte a todos os recursos.  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] dá suporte a objetos DOM, mas não a objetos definidos pelo usuário. Os atributos `enumerable` e `configurable` podem ser especificados, mas não são usados.  
  
## <a name="see-also"></a>Consulte também  
 [Protótipos de modelo de objeto de documento, parte 2: Acessador (getter/setter) suporte](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Função Object defineproperties](../../javascript/reference/object-defineproperties-function-javascript.md)   
 [Função Object.](../../javascript/reference/object-create-function-javascript.md)   
 [Função Object getownpropertydescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Função Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)