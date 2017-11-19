---
title: "Método Bind (Function) (JavaScript) | Microsoft Docs"
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
- parameters [JavaScript], bind method
- arguments [JavaScript], bind method
- bind method [JavaScript]
- this keyword [JavaScript], bind method
ms.assetid: 28946f47-b758-48cf-b508-610a0f2f6e19
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd7fc752df9bd41f8625ac2cb484486dfd19558d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="bind-method-function-javascript"></a>Método bind (Function) (JavaScript)
Para uma determinada função, cria uma função associada que tem o mesmo corpo da função original. Na função associada, o objeto `this` resolve para o que foi passado no objeto. A função associada possui os parâmetros iniciais especificados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
function.bind(thisArg[,arg1[,arg2[,argN]]])  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `function`  
 Necessário. Um objeto de função.  
  
 `thisArg`  
 Necessário. Um objeto ao qual a palavra-chave `this` pode fazer referência dentro da nova função.  
  
 `arg1`[,`arg2`[,`argN`]]]  
 Opcional. Uma lista de argumentos a serem transmitidos para a nova função.  
  
## <a name="return-value"></a>Valor de retorno  
 Uma nova função idêntica à função `function`, exceto pelo objeto `thisArg` e os argumentos iniciais.  
  
## <a name="exceptions"></a>Exceções  
 Se a `function` especificada não for uma função, uma exceção `TypeError` será lançada.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como usar o método `bind`.  
  
```JavaScript  
// Define the original function.  
var checkNumericRange = function (value) {  
    if (typeof value !== 'number')  
        return false;  
    else  
        return value >= this.minimum && value <= this.maximum;  
}  
  
// The range object will become the this value in the callback function.  
var range = { minimum: 10, maximum: 20 };  
  
// Bind the checkNumericRange function.  
var boundCheckNumericRange = checkNumericRange.bind(range);  
  
// Use the new function to check whether 12 is in the numeric range.  
var result = boundCheckNumericRange (12);  
document.write(result);  
  
// Output: true  
```  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o objeto `thisArg` é diferente do objeto que contém o método original.  
  
```JavaScript  
// Create an object that contains the original function.  
var originalObject = {  
    minimum: 50,  
    maximum: 100,  
    checkNumericRange: function (value) {  
        if (typeof value !== 'number')  
            return false;  
        else  
            return value >= this.minimum && value <= this.maximum;  
    }  
}  
  
// Check whether 10 is in the numeric range.  
var result = originalObject.checkNumericRange(10);  
document.write(result + " ");  
// Output: false  
  
// The range object supplies the range for the bound function.  
var range = { minimum: 10, maximum: 20 };  
  
// Create a new version of the checkNumericRange function that uses range.  
var boundObjectWithRange = originalObject.checkNumericRange.bind(range);  
  
// Check whether 10 is in the numeric range.  
var result = boundObjectWithRange(10);  
document.write(result);  
// Output: true  
```  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como usar os argumentos `arg1[,arg2[,argN]]]`. A função associada usa os parâmetros especificados no método `bind` como o primeiro e o segundo parâmetros. Todos os parâmetros especificados quando a função associada é chamada são usados como o terceiro, o quarto (e assim por diante) parâmetros.  
  
```JavaScript  
// Define the original function with four parameters.  
var displayArgs = function (val1, val2, val3, val4) {  
    document.write(val1 + " " + val2 + " " + val3 + " " + val4);  
}  
  
var emptyObject = {};  
  
// Create a new function that uses the 12 and "a" parameters  
// as the first and second parameters.  
var displayArgs2 = displayArgs.bind(emptyObject, 12, "a");  
  
// Call the new function. The "b" and "c" parameters are used  
// as the third and fourth parameters.  
displayArgs2("b", "c");  
// Output: 12 a b c   
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Objeto de função](../../javascript/reference/function-object-javascript.md)   
 [Método Filter (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [Usando o método bind](../../javascript/advanced/using-the-bind-method-javascript.md)   
 [Aplicativo de exemplo de JavaScript Hilo (Windows Store)](http://hilojs.codeplex.com/SourceControl/latest)