---
title: "Embora a instrução (JavaScript) | Microsoft Docs"
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
- while_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- loop structures, while statements
- while statement
ms.assetid: d63777cf-0e1a-4555-8d3a-334381001f48
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de64bf9181a0fc86a528fa7af21216b99530f217
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="while-statement-javascript"></a>Instrução while (JavaScript)
Executa uma instrução ou uma série de instruções até que uma condição especificada seja `false`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
while (expression) {  
    statements  
}   
```  
  
## <a name="parameters"></a>Parâmetros  
 `expression`  
 Necessário. Uma expressão booleana que é verificada antes de cada iteração do loop. Se `expression` é `true`, o loop é executado. Se `expression` é `false`, o loop é encerrado.  
  
 `statements`  
 Opcional. Um ou mais instruções a serem executadas se `expression` é `true`.  
  
## <a name="remarks"></a>Comentários  
 O `while` verificações de instrução `expression` antes de um loop é executado pela primeira vez. Se `expression` está `false` neste momento, o loop nunca será executado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da instrução `while`.  
  
```JavaScript  
var i = 0;  
var j = 10;  
while (i < 100) {  
    if (i == j)  
        break;  
    i++;  
}  
document.write(i);  
  
// Output: 10  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução break](../../javascript/reference/break-statement-javascript.md)   
 [Instrução continue](../../javascript/reference/continue-statement-javascript.md)   
 [... While instrução](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [Instrução for](../../javascript/reference/for-statement-javascript.md)   
 [Instrução for...in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)