---
title: "função instrução (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: function_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- new operator
- declaring functions, syntax
- function statement
- declaring functions
ms.assetid: cc9cfd43-1305-41c8-ad67-545d20f4fafe
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5fac3647e9374a9c909a420b73b86354cac69b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="function-statement-javascript"></a>Instrução Function (JavaScript)
Declara uma nova função.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
function functionname ([arg1 [, arg2 [,...[, argN]]]]) {  
    statements  
}   
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionname`  
 Necessário. O nome da função.  
  
 `arg1...argN`  
 Opcional. Uma lista opcional, separada por vírgula, de argumentos que a função compreende.  
  
 `statements`  
 Opcional. Um ou mais[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] instruções.  
  
## <a name="remarks"></a>Comentários  
 Use o `function` instrução para declarar uma função para uso posterior. O código que está contido no `statements` não será executado até que a função é chamada de em outro lugar no script.  
  
 O [retornar](../../javascript/reference/return-statement-javascript.md) instrução é usada para retornar um valor da função. Você não precisa usar um `return` instrução; o programa retornarão quando atingir o final da função. Se nenhum `return` instrução é executada na função, ou se o `return` instrução não tem nenhuma expressão, a função retornará o valor `undefined`.  
  
> [!NOTE]
>  Quando você chama uma função, certifique-se de incluir os parênteses e os argumentos necessários. Chamando uma função sem parênteses retorna uma referência à função, não os resultados da função.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da instrução `function`.  
  
```JavaScript  
function myfunction (arg1, arg2) {  
    var r = arg1 * arg2;  
    return(r);  
}  
```  
  
## <a name="example"></a>Exemplo  
 Uma função pode ser atribuída a uma variável. Isso é ilustrado no exemplo a seguir.  
  
```JavaScript  
function AddFive(x) {  
    return x + 5;  
}  
  
function AddTen(x) {  
    return x + 10;  
}  
  
var condition = false;  
  
var MyFunc;  
if (condition) {  
    MyFunc = AddFive;  
}  
else {  
    MyFunc = AddTen;  
}  
  
var result = MyFunc(123);  
// Output: 133  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador new](../../javascript/reference/new-operator-decrementjavascript.md)