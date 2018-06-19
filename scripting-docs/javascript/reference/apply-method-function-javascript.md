---
title: Método Apply (Function) (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- apply
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Apply method
ms.assetid: b36df78e-b14b-46ca-b5cb-de752d80f40a
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a06a37006937b07214bf5a314d5151c3b658acf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633356"
---
# <a name="apply-method-function-javascript"></a>Método apply (Function) (JavaScript)
Chama a função, substituindo o objeto especificado para o `this` valor da função e a matriz especificada para os argumentos da função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
apply([thisObj[,argArray]])  
```  
  
## <a name="parameters"></a>Parâmetros  
 `thisObj`  
 Opcional. O objeto a ser usado como o `this` objeto.  
  
 `argArray`  
 Opcional. Um conjunto de argumentos a serem passados para a função.  
  
## <a name="remarks"></a>Comentários  
 Se `argArray` não é um objeto válido, ocorrerá um erro "Objeto esperado".  
  
 Se nem `argArray` nem `thisObj` são fornecidos, o original `this` o objeto é usado como `thisObj` e nenhum argumento for passado.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como usar o método apply.  
  
```JavaScript  
function callMe(arg1, arg2){  
    var s = "";  
  
    s += "this value: " + this;  
    s += "<br />";  
    for (i in callMe.arguments) {  
        s += "arguments: " + callMe.arguments[i];  
        s += "<br />";  
    }  
    return s;  
}  
  
document.write("Original function: <br/>");  
document.write(callMe(1, 2));  
document.write("<br/>");  
  
document.write("Function called with apply: <br/>");  
document.write(callMe.apply(3, [ 4, 5 ]));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with apply:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Function](../../javascript/reference/function-object-javascript.md)