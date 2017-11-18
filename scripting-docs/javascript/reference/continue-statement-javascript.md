---
title: "Instrução Continue (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: continue_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- do...while statement
- continue statement
- loop structures, continue statement
ms.assetid: f8a30d9f-e2de-4e1f-8668-4e4cf95f7df9
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 391f919c4d06a6c529bfee34e21ca7238b3c63b7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="continue-statement-javascript"></a>Instrução Continue (JavaScript)
Interrompe a iteração atual de um loop e inicia uma nova iteração.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
continue [label];  
```  
  
## <a name="remarks"></a>Comentários  
 Opcional `label` argumento especifica a instrução para o qual `continue` se aplica.  
  
 Você pode usar o `continue` instrução somente dentro um `while`, `do...while`, **para**, ou `for...in` loop. Executar o `continue` instrução interrompe a iteração atual do loop e continua o fluxo de programa com o início do loop. Isso tem os seguintes efeitos sobre os diferentes tipos de loops de:  
  
-   `while`e `do...while` loops sua condição de teste e, se for true, execute o loop novamente.  
  
-   `for`loops executar sua expressão de incremento e se a expressão for verdadeira, execute o loop novamente.  
  
-   `for...in`loops prosseguir para o próximo campo da variável especificada e execute o loop novamente.  
  
## <a name="examples"></a>Exemplos  
 Neste exemplo, um loop itera de 1 a 9. As instruções entre `continue` e o término do `for` corpo são ignorados devido ao uso o `continue` instrução junto com a expressão `(i < 5)`.  
  
```JavaScript  
for (var i = 1; i < 10; i++) {  
    if (i < 5) {  
        continue;  
    }  
    document.write (i);  
    document.write (" ");  
}  
  
// Output: 5 6 7 8 9  
```  
  
 No código a seguir, o `continue` instrução refere-se para o `for` loop que é precedido pelo `Inner:` rótulo. Quando `j` é 24, o `continue` instrução faz com que que `for` loop para ir para a próxima iteração. Os números de 21 a 23 e 25 a 30 impressos em cada linha.  
  
```JavaScript  
Outer:  
for (var i = 1; i <= 10; i++) {  
    document.write ("<br />");  
    document.write ("i: " + i);  
    document.write (" j: ");  
  
Inner:  
    for (var j = 21; j <= 30; j++) {  
        if (j == 24) {  
             continue Inner;  
        }  
        document.write (j + " ");  
    }  
}  
  
//Output:  
//i: 1 j: 21 22 23 25 26 27 28 29 30   
//i: 2 j: 21 22 23 25 26 27 28 29 30   
//i: 3 j: 21 22 23 25 26 27 28 29 30   
//i: 4 j: 21 22 23 25 26 27 28 29 30   
//i: 5 j: 21 22 23 25 26 27 28 29 30   
//i: 6 j: 21 22 23 25 26 27 28 29 30   
//i: 7 j: 21 22 23 25 26 27 28 29 30   
//i: 8 j: 21 22 23 25 26 27 28 29 30   
//i: 9 j: 21 22 23 25 26 27 28 29 30   
//i: 10 j: 21 22 23 25 26 27 28 29 30  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução break](../../javascript/reference/break-statement-javascript.md)   
 [... While instrução](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [Instrução for](../../javascript/reference/for-statement-javascript.md)   
 [loop for... na instrução](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Instrução rotulada](../../javascript/reference/labeled-statement-javascript.md)   
 [Instrução while](../../javascript/reference/while-statement-javascript.md)