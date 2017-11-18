---
title: "Instrução for (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: for_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: loop structures, for statements
ms.assetid: bae0ec40-152e-43f3-969b-3696489ec5c4
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7142dbb8c00a351918d0821c3ca7dba3d7b2acb6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="for-statement-javascript"></a>Instrução for (JavaScript)
Executa um bloco de instruções enquanto uma condição especificada for verdadeira.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
for ([initialization]; [test]; [increment])  
   statement   
```  
  
## <a name="parameters"></a>Parâmetros  
 `initialization`  
 Opcional. Uma expressão. Essa expressão é executada apenas uma vez, antes que o loop é executado.  
  
 `test`  
 Opcional. Uma expressão booleana. Se `test` é `true`, `statement` é executado. Se `test` se `false`, o loop é encerrado.  
  
 `increment`  
 Opcional. Uma expressão. A expressão de incremento é executado no final de cada passagem do loop.  
  
 `statement`  
 Opcional. Um ou mais instruções a serem executadas se `test` é **true**. Pode ser uma instrução composta.  
  
## <a name="remarks"></a>Comentários  
 Você geralmente usa um `for` loop quando o loop for para ser executado várias vezes conhecidas. Um `for` loop é útil para iterar em matrizes e para executar processamento sequencial.  
  
 O teste de uma expressão condicional ocorre antes da execução do loop, então um `for` instrução executa zero ou mais vezes.  
  
 Em qualquer linha em uma `for` bloco de instruções de loop, você pode usar o `break` instrução para sair do loop, ou você pode usar o `continue` instrução para transferir controle para a próxima iteração do loop.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o `for` instrução executa as instruções da seguinte maneira:  
  
-   Primeiro, o valor inicial da variável `i` é avaliada.  
  
-   Em seguida, desde que o valor de `i` é menor ou igual a 9, o `document.write` instruções são executadas e `i` é reavaliado.  
  
-   Quando `i` é maior do que 9, a condição for false e o controle é transferido fora do loop.  
  
```JavaScript  
// i is set to 0 at the start and is incremented by 1 at the  
// end of each iteration.  
// The loop terminates when i is not less than or equal to  
// 9 before a loop iteration.  
for (var i = 0; i <= 9; i++) {  
   document.write (i);  
   document.write (" ");  
}  
  
// Output: 0 1 2 3 4 5 6 7 8 9  
```  
  
## <a name="example"></a>Exemplo  
 Todas as expressões do `for` instrução são opcionais. No exemplo a seguir, o `for` instruções criam um loop infinito e um `break` instrução é usada para sair do loop.  
  
```JavaScript  
var j = 0;  
for (;;) {  
    if (j >= 5) {  
        break;  
    }  
    j++;  
    document.write (j + " ");  
}  
  
// Output: 1 2 3 4 5  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [loop for... na instrução](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [Instrução while](../../javascript/reference/while-statement-javascript.md)