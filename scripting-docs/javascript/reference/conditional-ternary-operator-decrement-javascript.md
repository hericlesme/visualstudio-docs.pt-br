---
title: "Operador condicional (Ternário) (?) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '?:'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional operators
- conditional (Ternary) operator
- ternary
ms.assetid: 7399ac32-9324-4a9a-ae76-be9c0f9df81c
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dc34b5c633cfc02219cb01061e1aaa017e0f7f2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="conditional-ternary-operator--javascript"></a>Operador condicional (Ternário) (?:) (JavaScript)
Retorna uma de duas expressões, dependendo de uma condição.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
test ? expression1 : expression2  
```  
  
## <a name="parameters"></a>Parâmetros  
 `test`  
 Qualquer expressão booliana.  
  
 `expression1`  
 Uma expressão retornada se `test` for `true`. Pode ser uma expressão com vírgulas.  
  
 `expression2`  
 Uma expressão retornada se `test` for `false`. Mais de uma expressão podem ser vinculadas por uma expressão com vírgulas.  
  
## <a name="remarks"></a>Comentários  
 O operador `?:` pode ser usado como atalho para uma instrução `if...else`. Em geral, ele é usado como parte de uma expressão maior, na qual uma instrução `if...else` seria impraticável. Por exemplo:  
  
```JavaScript  
var now = new Date();  
var greeting = "Good" + ((now.getHours() > 17) ? " evening." : " day.");  
```  
  
 O exemplo cria uma cadeia de caracteres contendo "Bom evening." Se ele é após 6 horas. O código equivalente usando uma instrução `if...else` seria semelhante ao seguinte:  
  
```JavaScript  
var now = new Date();  
var greeting = "Good";  
if (now.getHours() > 17)  
   greeting += " evening.";  
else  
   greeting += " day.";  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [If... instrução else](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)   
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)   
 [Aplicativo de exemplo do Script Junkie configuração widget](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)