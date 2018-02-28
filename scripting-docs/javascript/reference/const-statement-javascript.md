---
title: "Instrução Const (JavaScript) | Microsoft Docs"
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
- const_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- declaring variables, const statement
- const statement
ms.assetid: 3ad0840f-437f-4163-9571-86ecc5ddb987
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68130cec4f1b1fe89d2fe3e673b28963d79aebde
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="const-statement-javascript"></a>Instrução const (JavaScript)
Declara uma variável de escopo de bloco com um valor constante.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
const constant1 = value1  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `constant1`  
 O nome da variável que está sendo declarado.  
  
 `value1`  
 O valor inicial atribuído à variável.  
  
## <a name="remarks"></a>Comentários  
 Use o `const` instrução para declarar uma variável com um valor constante, o escopo do qual é restrito para o bloco no qual ela é declarada. O valor da variável não pode ser alterado.  
  
 Uma variável declarada usando `const` devem ser inicializados quando ela é declarada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da instrução `const`.  
  
```JavaScript  
var c = 10;  
{  
    const c = 2;  
   // At this point, c = 2.  
}  
// At this point, c = 10.  
  
// Additional ways to declare a variable using const.  
const name = "Thomas Jefferson";  
const answer = 42, numpages = 10;  
const myarray = new Array();  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Let](../../javascript/reference/let-statement-javascript.md)   
 [Operador new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Objeto Array](../../javascript/reference/array-object-javascript.md)   
 [Variáveis](../../javascript/variables-javascript.md)