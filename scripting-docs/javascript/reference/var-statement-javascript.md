---
title: "Instrução var (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/22/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- var_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- declaring variables, var statement
- var statement
ms.assetid: 56f900af-a5c4-4667-9664-5956d30f0aae
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839b6904fa59b6f4ea9a5c4d8e00213cd351517a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="var-statement-javascript"></a>Instrução var (JavaScript)
Declara uma variável.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
var variable1 = value1  
```  
  
## <a name="parameters"></a>Parâmetros  
 `variable1`  
 O nome da variável que está sendo declarado.  
  
 `value1`  
 O valor inicial atribuído à variável.  
  
## <a name="remarks"></a>Comentários  
 Use o `var` instrução para declarar variáveis. Você pode atribuir valores às variáveis quando você declará-los ou posteriormente no script.  
  
 Uma variável é declarada na primeira vez que ele aparece em seu script.  
  
 Você pode declarar uma variável sem usar o `var` palavra-chave e atribuir um valor a ele. Isso é conhecido como um *declaração implícita*, e não é recomendado. Uma declaração implícita fornece o escopo da variável global. Quando você declara uma variável no nível de procedimento, no entanto, você normalmente não deseja têm escopo global. Para evitar conceder o escopo da variável global, você deve usar o `var` palavra-chave em sua declaração de variável.  
  
 Se você não inicializar a variável no `var` instrução, ele é automaticamente atribuído a [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valor `undefined`.  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir ilustram o uso do `var` instrução.  
  
```JavaScript  
var index;  
var name = "Thomas Jefferson";  
var answer = 42, counter, numpages = 10;  
var myarray = new Array();  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Function](../../javascript/reference/function-statement-javascript.md)   
 [Operador new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Objeto Array](../../javascript/reference/array-object-javascript.md)   
 [Variáveis](../../javascript/variables-javascript.md)