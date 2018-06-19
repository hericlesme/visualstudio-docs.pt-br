---
title: Função Object getownpropertynames (JavaScript) | Microsoft Docs
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
- getOwnPropertyNames method [JavaScript]
- Object.getOwnPropertyNames method [JavaScript]
ms.assetid: 59f4b6b1-02be-44b3-a06c-a5ca8f70c3d8
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76ca0036b9dedf7b4cee7b543469939e35dfe8d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639926"
---
# <a name="objectgetownpropertynames-function-javascript"></a>Função Object.getOwnPropertyNames (JavaScript)
Retorna os nomes das próprias propriedades de um objeto. As próprias propriedades de um objeto são aqueles que são definidos diretamente no objeto e não são herdadas do protótipo do objeto. As propriedades de um objeto incluem funções e campos (objetos).  
  
## <a name="syntax"></a>Sintaxe  
  
```JavaScript  
Object.getOwnPropertyNames(object)  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Definição|  
|---------------|----------------|  
|`object`|Necessário. O objeto que contém as propriedades próprias.|  
  
## <a name="return-value"></a>Valor de retorno  
 Uma matriz que contém os nomes das propriedades próprios do objeto.  
  
## <a name="exceptions"></a>Exceções  
 Se o valor fornecido para o `object` argumento não é o nome de um objeto, um `TypeError` exceção será lançada.  
  
## <a name="remarks"></a>Comentários  
 O `getOwnPropertyNames` método retorna os nomes de propriedades enumeráveis e não enumeráveis e métodos. Para retornar somente os nomes dos métodos e propriedades enumeráveis, você pode usar o [função Object Keys](../../javascript/reference/object-keys-function-javascript.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um objeto que tem três propriedades e um método. Ele usa o `getOwnPropertyNames` método para obter as propriedades próprias (incluindo o método) do objeto.  
  
```JavaScript  
function Pasta(grain, width, shape) {  
    // Define properties.  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Get the own property names.  
var arr = Object.getOwnPropertyNames(spaghetti);  
document.write (arr);  
  
// Output:  
//   grain,width,shape,toString  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir exibe os nomes das propriedades que começam com a letra ' em um **espaguete** objeto construído com o **massas** construtor.  
  
```JavaScript  
function Pasta(grain, size, shape) {  
    this.grain = grain;   
    this.size = size;   
    this.shape = shape;   
}  
  
var spaghetti = new Pasta("wheat", 2, "circle");  
  
var names = Object.getOwnPropertyNames(spaghetti).filter(CheckKey);  
document.write(names);   
  
// Check whether the first character of a string is 's'.   
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);   
    if (firstChar.toLowerCase() == 's')  
        return true;   
    else  
         return false;   
}  
// Output:  
// size,shape  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função Object.keys](../../javascript/reference/object-keys-function-javascript.md)