---
title: Função Object Create (JavaScript) | Microsoft Docs
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
- create function [JavaScript]
- Object.create function [JavaScript]
ms.assetid: 0ad31f36-a9ee-444e-b0fe-c87843d03196
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f359908c5c836743e22390580f542df27d7b98e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640476"
---
# <a name="objectcreate-function-javascript"></a>Função Object.create (JavaScript)
Cria um objeto que tem o protótipo especificado e, opcionalmente, contendo propriedades especificadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Object.create(prototype, descriptors)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `prototype`  
 Necessário. O objeto a ser usado como um protótipo. Pode ser `null`.  
  
 `descriptors`  
 Opcional. Um [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] objeto que contém um ou mais descritores de propriedade.  
  
 Um *propriedade dados* é uma propriedade que pode obter e definir um valor. Um descritor de propriedade de dados contém um `value` atributo, além de `writable`, `enumerable`, e `configurable` atributos. Se os três atributos não forem especificados, eles padrão `false`. Um *propriedade do acessador* chama uma função fornecida pelo usuário toda vez que o valor é recuperado ou definido. Um descritor de propriedade do acessador contém um `set` atributo, um `get` atributo, ou ambos. Para obter mais informações, consulte [função Object defineproperty](../../javascript/reference/object-defineproperty-function-javascript.md).  
  
## <a name="return-value"></a>Valor de retorno  
 Um novo objeto que tem o protótipo interno especificado e contém as propriedades especificadas, se houver.  
  
## <a name="exceptions"></a>Exceções  
 Um `TypeError` exceção será lançada se qualquer uma das seguintes condições for verdadeira:  
  
-   O `prototype` argumento não é um objeto e não é `null`.  
  
-   Descritor de uma a `descriptors` argumento tem uma `value` ou `writable` de atributos e tem um `get` ou `set` atributo.  
  
-   Descritor de uma a `descriptors` argumento tem uma `get` ou `set` atributo que não é uma função.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar essa função usando um `null``prototype` parâmetro para interromper a cadeia de protótipos. O objeto criado não terá nenhum protótipo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um objeto usando um `null` protótipo e adiciona duas propriedades enumeráveis.  
  
```JavaScript  
var newObj = Object.create(null, {  
            size: {  
                value: "large",  
                enumerable: true  
            },  
            shape: {  
                value: "round",  
                enumerable: true  
            }  
        });  
  
document.write(newObj.size + "<br/>");  
document.write(newObj.shape + "<br/>");  
document.write(Object.getPrototypeOf(newObj));  
  
// Output:  
// large  
// round  
// null  
  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um objeto que tem o mesmo protótipo interno como o objeto. Você pode ver que tem o mesmo protótipo como um objeto criado usando um literal de objeto. O [getprototypeof](../../javascript/reference/object-getprototypeof-function-javascript.md) função obtém o protótipo do objeto original. Para obter o descritor de propriedade do objeto, você pode usar [função Object getownpropertydescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
```JavaScript  
var firstLine = { x: undefined, y: undefined };  
  
var secondLine = Object.create(Object.prototype, {  
        x: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            },  
            y: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            }  
});  
  
document.write("first line prototype = " + Object.getPrototypeOf(firstLine));  
document.write("<br/>");  
document.write("second line prototype = " + Object.getPrototypeOf(secondLine));  
  
// Output:  
// first line prototype = [object Object]  
// second line prototype = [object Object]  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um objeto que tem o mesmo protótipo interno que o objeto de forma.  
  
```JavaScript  
  
// Create the shape object.  
var Shape = { twoDimensional: true, color: undefined, hasLineSegments: undefined };  
  
var Square = Object.create(Object.getPrototypeOf(Shape));  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função Object. getprototypeof](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [Método isPrototypeOf (Object)](../../javascript/reference/isprototypeof-method-object-javascript.md)   
 [Criar objetos](../../javascript/creating-objects-javascript.md)