---
title: Método Call (Function) (JavaScript) | Microsoft Docs
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
- call
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- call method
ms.assetid: fa356dec-48e6-4f75-8bf3-c1814a76818f
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ef871f85459ad875a747ae79c7c054b30a82e55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634106"
---
# <a name="call-method-function-javascript"></a>Método call (Function) (JavaScript)
Chama um método de um objeto, substituindo a outro objeto para o objeto atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
call([thisObj[, arg1[, arg2[,  [, argN]]]]])  
```  
  
## <a name="parameters"></a>Parâmetros  
 `thisObj`  
 Opcional. O objeto a ser usado como o objeto atual.  
  
 `arg1, arg2, , argN`  
 Opcional. Uma lista de argumentos a serem passados para o método.  
  
## <a name="remarks"></a>Comentários  
 O `call` método é usado para chamar um método em nome de outro objeto. Permite que você altere o `this` o objeto de uma função do contexto original para o novo objeto especificado pelo `thisObj`.  
  
 Se `thisObj` não for fornecido, o `global` o objeto é usado como `thisObj`.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como usar o método `call`.  
  
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
  
document.write("Function called with call: <br/>");  
document.write(callMe.call(3, 4, 5));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with call:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Objeto de função](../../javascript/reference/function-object-javascript.md)   
 [Método apply (Function)](../../javascript/reference/apply-method-function-javascript.md)