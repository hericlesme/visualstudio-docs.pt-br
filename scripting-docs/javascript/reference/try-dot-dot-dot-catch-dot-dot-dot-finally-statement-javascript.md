---
title: "Try...... finally instrução catch (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- try_JavaScriptKeyword
- finally_JavaScriptKeyword
- catch_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- try-catch exception handling, finally block
- try-catch exception handling, about try-catch exception handling
- try-catch exception handling, catch block
- try-catch exception handling
ms.assetid: b7a0a54e-dfaa-4e41-bf25-bcaa43e601fb
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b05f15e593aeb7cb921f6237fad30b589cfdfe66
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="trycatchfinally-statement-javascript"></a>Instrução try...catch...finally (JavaScript)
Configura blocos de código em que os erros gerados em um bloco são manipulados em outro. Os erros gerados no bloco `try` são capturados no bloco `catch`. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```  
try {  
    tryStatements  
}  
catch(exception){  
    catchStatements  
}  
finally {  
    finallyStatements  
}  
```  
  
## <a name="parameters"></a>Parâmetros  
 `tryStatements`  
 Necessário. Instruções em que um erro pode ocorrer.  
  
 `exception`  
 Necessário. Qualquer nome de variável. O valor inicial de `exception` é o valor do erro gerado.  
  
 `catchStatements`  
 Opcional. Instruções para manipular erros que ocorrem no `tryStatements` associado.  
  
 `finallyStatements`  
 Opcional. Instruções que são executadas incondicionalmente após a conclusão de todos os outros processamentos de erros.  
  
## <a name="remarks"></a>Comentários  
 A instrução `try...catch...finally` oferece uma maneira de lidar com alguns ou com todos os erros que podem ocorrer em um determinado bloco de código e, ainda assim, executar o código. Se houver erros não manipulados, o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] fornecerá a mensagem de erro normal.  
  
 O bloco `try` contém código que pode provocar um erro, enquanto que o bloco `catch` contém o código que manipula alguns ou todos os erros. Se um erro ocorrer no bloco `try`, o controle do programa será passado para o bloco `catch`. O valor de `exception` é o valor do erro que ocorreu no bloco `try`. Se nenhum erro ocorrer, o código do bloco `catch` nunca será executado.  
  
 Você pode passar o erro até o próximo nível usando a instrução `throw` para gerar o erro novamente.  
  
 Depois que todas as instruções do bloco `try` tiverem sido executadas e o tratamento de erro tiver sido feito no bloco `catch`, as instruções no bloco `finally` serão executadas, independentemente se um erro foi ou não tratado. O código no `finally` bloco sempre é executado a menos que ocorra um erro não tratado (por exemplo, um erro em tempo de execução dentro do **catch** bloco).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir faz com que uma exceção `ReferenceError` seja gerada e exibe o nome do erro e sua mensagem.  
  
```JavaScript  
try {  
    addalert("bad call");  
}  
catch(e) {  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF);  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
  
// Output:  
Error Message: 'addalert' is undefined  
Error Code: 5009  
Error Name: ReferenceError  
  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como gerar erros novamente, bem como a execução de blocos `try...catch` aninhados. Quando o erro é gerado no bloco `try` aninhado, ele é passado para o bloco `catch` aninhado, que o gera novamente. O bloco `finally` aninhado é executado antes que o bloco externo `catch` trate o erro, e no final da execução do bloco `finally` externo.  
  
```JavaScript  
try {  
    document.write("Outer try running...<br/>");  
  
    try {  
        document.write("Nested try running...<br/>");  
        throw new Error(301, "an error");  
    }  
    catch (e) {  
        document.write ("Nested catch caught " + e.message + "<br/>");  
        throw e;  
    }  
    finally {  
        document.write ("Nested finally is running...<br/>");  
    }  
}  
catch (e) {  
    document.write ("Outer catch caught " + e.message + "<br/>");  
}  
finally {  
    document.write ("Outer finally running");  
}  
  
// Output:  
// Outer try running...  
// Nested try running...  
// Nested catch caught error from nested try  
// Nested finally is running...  
// Outer catch caught error from nested try  
// Outer finally running  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
> [!NOTE]
>  Começando com o modo de padrões do Internet Explorer 8, o **catch** bloco não é mais necessário para `finally` para executar.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução throw](../../javascript/reference/throw-statement-javascript.md)   
 [Aplicativo de exemplo do Assistente de configuração do Script Junkie](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)