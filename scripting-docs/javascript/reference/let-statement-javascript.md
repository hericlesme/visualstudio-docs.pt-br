---
title: "Instrução Let (JavaScript) | Microsoft Docs"
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
- let_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- let statement
- declaring variables, let statement
ms.assetid: c7e4f8a9-8f54-47b6-aed2-956959c1ecfd
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c447a1bf0c430771ff146965a592f7e160e2055b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="let-statement-javascript"></a>Instrução let (JavaScript)
Declara uma variável de escopo de bloco.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
let variable1 = value1  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `variable1`  
 O nome da variável que está sendo declarado.  
  
 `value1`  
 O valor inicial atribuído à variável.  
  
## <a name="remarks"></a>Comentários  
 Use o `let` instrução para declarar uma variável, o escopo do qual é restrito para o bloco no qual ela é declarada. Você pode atribuir valores às variáveis quando você declará-los ou posteriormente no script.  
  
 Uma variável declarada usando `let` não pode ser usado antes de que resultará um erro ou sua declaração.  
  
 Se você não inicializar a variável no `let` instrução, ele é automaticamente atribuído a [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valor `undefined`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso da instrução `let`.  
  
```JavaScript  
var  l = 10;  
{  
    let l = 2;  
   // At this point, l = 2.  
}  
// At this point, l = 10.  
  
// Additional ways to declare a variable using let.  
let index;  
let name = "Thomas Jefferson";  
let answer = 42, counter, numpages = 10;  
let myarray = new Array();  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Const](../../javascript/reference/const-statement-javascript.md)   
 [Operador new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Objeto Array](../../javascript/reference/array-object-javascript.md)   
 [Variáveis](../../javascript/variables-javascript.md)