---
title: "Instrução throw (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: throw_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- error handling, throw statement
- throw statement
ms.assetid: 75cbade0-fb81-4ffe-b187-b71be380bb05
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7cedecec1c5f13e1aba07273c1e3deca4f835429
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="throw-statement-javascript"></a>Instrução throw (JavaScript)
Gera uma condição de erro que pode ser tratada por um `try...catch...finally` instrução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
throw exception   
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `exception` argumento pode ser qualquer expressão.  
  
 O exemplo a seguir gera um erro dentro de um `try` bloco e ele é detectado no `catch` bloco.  
  
```JavaScript  
try {  
        throw new Error(200, "x equals zero");  
}  
catch (e) {  
    document.write(e.message);  
}  
  
// Output: x equals zero.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Try...... finally instrução catch](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Objeto Error](../../javascript/reference/error-object-javascript.md)