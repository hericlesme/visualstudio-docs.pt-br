---
title: Erros de sintaxe JavaScript | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- errors [JavaScript]
- syntax errors, JavaScript
ms.assetid: 0343dc19-5f5e-4a4c-83da-630b4fbcb3b6
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3bc3398d6a90ef308fd2b4b367bc1006ad95f5b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="javascript-syntax-errors"></a>Erros de sintaxe JavaScript
[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]erros de sintaxe ocorrem quando a estrutura de um dos seus [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] instruções viola uma ou mais das regras de sintaxe.  
  
## <a name="errors"></a>Erros  
  
|Número do erro|Descrição|  
|------------------|-----------------|  
|1019|[Não é possível ter 'break' fora do loop](../../javascript/misc/can-t-have-break-outside-of-loop.md)|  
|1020|[Não é possível ter 'continue' fora do loop](../../javascript/misc/can-t-have-continue-outside-of-loop.md)|  
|1030|[Compilação condicional está desativada](../../javascript/misc/conditional-compilation-is-turned-off.md)|  
|1027|['default' só pode aparecer em uma instrução 'switch'](../../javascript/misc/default-can-only-appear-once-in-a-switch-statement.md)|  
|1005|[Esperado ' ('](../../javascript/misc/expected-left-parenthesis-javascript.md)|  
|1006|[Esperado ')'](../../javascript/misc/expected-right-parenthesis-javascript.md)|  
|1012|[Esperado '/'](../../javascript/misc/expected-minus.md)|  
|1003|[':' esperado](../../javascript/misc/expected-colon.md)|  
|1004|[';' esperado](../../javascript/misc/expected-semicolon.md)|  
|1032|['@' esperado](../../javascript/misc/expected-at.md)|  
|1029|['@end' esperado](../../javascript/misc/expected-at-end.md)|  
|1007|[Esperado ' &#93;'](../../javascript/misc/expected-right-square-bracket.md)|  
|1008|[Esperado '{'](../../javascript/misc/expected-left-curly-brace.md)|  
|1009|['}' esperado](../../javascript/misc/expected-right-curly-brace.md)|  
|1011|['=' Esperado](../../javascript/misc/expected-equal-javascript.md)|  
|1033|['catch' esperado](../../javascript/misc/expected-catch.md)|  
|1031|[Constante esperada](../../javascript/misc/expected-constant.md)|  
|1023|[Dígito hexadecimal esperado](../../javascript/misc/expected-hexadecimal-digit.md)|  
|1010|[Identificador esperado](../../javascript/misc/expected-identifier-javascript.md)|  
|1028|[Identificador, cadeia de caracteres ou número esperado](../../javascript/misc/expected-identifier-string-or-number.md)|  
|1024|['while' esperado](../../javascript/misc/expected-while.md)|  
|1014|[Caractere inválido](../../javascript/misc/invalid-character-javascript.md)|  
|1026|[Rótulo não encontrado](../../javascript/misc/label-not-found.md)|  
|1025|[Rótulo redefinido](../../javascript/misc/label-redefined.md)|  
|1018|[Instrução 'return' fora de função](../../javascript/misc/return-statement-outside-of-function.md)|  
|1002|[Erro de sintaxe](../../javascript/misc/syntax-error-javascript.md)|  
|1035|[O lançamento deve ser seguido por uma expressão na mesma linha de origem](../../javascript/misc/throw-must-be-followed-by-an-expression-on-the-same-source-line.md)|  
|1016|[Comentário não finalizado](../../javascript/misc/unterminated-comment.md)|  
|1015|[Constante de cadeia de caracteres não finalizada](../../javascript/misc/unterminated-string-constant-javascript.md)|  
  
### <a name="script-host-errors"></a>Erros de Host de script  
 Os erros a seguir estão falando corretamente os erros relacionados ao host de script, mas você pode vê-los ocasionalmente.  
  
|Erro|HRESULT|Descrição|  
|-----------|-------------|-----------------|  
|SCRIPT_E_RECORDED|0x86664004|Um erro foi registrado para ser transmitidos entre o host e o mecanismo de script. O host precisa passar o código de erro para o chamador.|  
|SCRIPT_E_REPORTED|0x80020101|Mecanismo de script relatou uma exceção sem tratamento ao host por meio de IActiveScriptSite::OnScriptError. Host pode ignorar esse erro.|  
|SCRIPT_E_PROPAGATE|0x8002010|Um erro de script está sendo propagado ao chamador que pode estar em um thread diferente. O host deve passar o código de erro para o chamador.|  
  
## <a name="see-also"></a>Consulte também  
 [Erros de tempo de execução JavaScript](../../javascript/reference/javascript-run-time-errors.md)