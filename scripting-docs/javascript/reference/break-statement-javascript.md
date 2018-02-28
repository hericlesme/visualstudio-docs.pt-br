---
title: "Instrução break (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- break_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- break statement
ms.assetid: 5be0f2a8-5fe7-4a6c-89af-ca20a925ce87
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f085a4e51309bf9a060e9ffa352c6ae85924237
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="break-statement-javascript"></a>Instrução break (JavaScript)
Encerra o loop atual, ou em conjunto com um `label`, termina a instrução associada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
break [label];  
```  
  
## <a name="remarks"></a>Comentários  
 Opcional `label` argumento especifica o rótulo da instrução são as recentes do.  
  
 Você normalmente usa o `break` instrução em `switch` instruções e, em `while`, `for`, `for...in`, ou `do...while` loops. Você geralmente usa o `label` argumento `switch` instruções, mas ele pode ser usado em qualquer instrução simples ou composta.  
  
 Executar o `break` instrução sai do loop atual ou instrução e começa a execução do script com a instrução imediatamente posterior.  
  
## <a name="examples"></a>Exemplos  
 Neste exemplo, o contador está definido para contagem de 1 a 99; No entanto, o `break` instrução encerra o loop depois de 14 contagens.  
  
```JavaScript  
for (var i = 1; i < 100; i++) {  
    if (i == 15) {  
        break;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 1234567891011121314  
```  
  
 No código a seguir, o `break` instrução refere-se para o `for` loop que é precedido pelo `Inner:` instrução. Quando `j` é igual a 24, o `break` instrução faz com que o fluxo de programa sair do loop. Os números de 21 a 23 impressos em cada linha.  
  
```JavaScript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
            break Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
// Output:   
// i: 1 j: 21 22 23   
// i: 2 j: 21 22 23   
// i: 3 j: 21 22 23   
// i: 4 j: 21 22 23   
// i: 5 j: 21 22 23   
// i: 6 j: 21 22 23   
// i: 7 j: 21 22 23   
// i: 8 j: 21 22 23   
// i: 9 j: 21 22 23   
// i: 10 j: 21 22 23  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução continue](../../javascript/reference/continue-statement-javascript.md)   
 [... While instrução](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [Instrução for](../../javascript/reference/for-statement-javascript.md)   
 [loop for... na instrução](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Instrução rotulada](../../javascript/reference/labeled-statement-javascript.md)   
 [Instrução while](../../javascript/reference/while-statement-javascript.md)