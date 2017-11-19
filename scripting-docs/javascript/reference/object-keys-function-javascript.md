---
title: "Função Object Keys (JavaScript) | Microsoft Docs"
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
- Object.keys method [JavaScript]
- keys method [JavaScript]
ms.assetid: cf4a7daf-cf28-4467-bc6b-f7f106ec3876
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e725c3ab7206b04d9a900cb614b57c37dfc4351
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="objectkeys-function-javascript"></a>Função Object.keys (JavaScript)
Retorna os nomes das propriedades e métodos enumeráveis um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
Object.keys(object)  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Definição|  
|---------------|----------------|  
|`object`|Necessário. O objeto que contém as propriedades e métodos. Isso pode ser um objeto de modelo de objeto de documento (DOM) existente ou de um objeto que você criou.|  
  
## <a name="return-value"></a>Valor de retorno  
 Uma matriz que contém os nomes das propriedades enumeráveis e métodos do objeto.  
  
## <a name="exceptions"></a>Exceções  
 Se o valor fornecido para o `object` argumento não é o nome de um objeto, um `TypeError` exceção será lançada.  
  
## <a name="remarks"></a>Comentários  
 O `keys` método retorna apenas os nomes dos métodos e propriedades enumeráveis. Para retornar os nomes das propriedades enumeráveis e não enumeráveis e métodos, você pode usar [função Object getownpropertynames](../../javascript/reference/object-getownpropertynames-function-javascript.md).  
  
 Para obter informações sobre o `enumerable` atributo de uma propriedade, consulte [função Object defineproperty](../../javascript/reference/object-defineproperty-function-javascript.md) e [função Object getownpropertydescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um objeto que tem três propriedades e um método. Ele usa o `keys` método para obter as propriedades e métodos do objeto.  
  
```JavaScript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
  
    // Define a method.  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Put the enumerable properties and methods of the object in an array.  
var arr = Object.keys(spaghetti);  
document.write (arr);  
  
// Output:  
// grain,width,shape,toString  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir exibe os nomes de todas as propriedades enumeráveis que começam com a letra "g" no objeto de Pasta.  
  
```JavaScript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
}  
  
var polenta = new Pasta("corn", 1, "mush");  
  
var keys = Object.keys(polenta).filter(CheckKey);  
document.write(keys);  
  
// Check whether the first character of a string is "g".  
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);  
    if (firstChar.toLowerCase() == "g")  
        return true;  
    else  
        return false;  
}  
  
// Output:  
// grain  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)