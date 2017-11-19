---
title: Operador typeof (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: typeof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: typeof operator
ms.assetid: ee8a1036-119f-486f-b034-b07bdba87f0c
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c79c69e6c447b14e61fa67ccb8600d5d83bebd2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="typeof-operator-javascript"></a>Operador typeof (JavaScript)
Retorna uma cadeia de caracteres que identifica o tipo de dados de uma expressão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
typeof[(]expression[)] ;  
```  
  
## <a name="remarks"></a>Comentários  
 O *expressão* argumento é qualquer expressão para qual tipo de informações são pesquisadas.  
  
 O `typeof` operador retorna informações de tipo como uma cadeia de caracteres. Há seis possíveis valores que `typeof` retorna: "number", "cadeia de caracteres," ",""objeto boolean," "função" e "indefinida".  
  
 Os parênteses são opcionais no `typeof` sintaxe.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir testa o tipo de dados de variáveis.  
  
```JavaScript  
var index = 5;  
var result = (typeof index === 'number');  
// Output: true  
  
var description = "abc";  
var result = (typeof description === 'string');  
// Output: true  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir testa para um tipo de dados `undefined` variáveis declaradas e não declarado.  
  
```JavaScript  
var declared;  
var result = (declared === undefined);  
// Output: true  
  
var result = (typeof declared === 'undefined');  
// Output: true  
  
var result = (typeof notDeclared === 'undefined')  
// Output: true  
  
var obj = {};  
var result = (typeof obj.propNotDeclared === 'undefined');  
// Output: true  
  
// An undeclared variable cannot be used in a comparison without  
// the typeof operator, so the next line generates an error.  
//  var result = (notDeclared === undefined);  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função array. IsArray](../../javascript/reference/array-isarray-function-javascript.md)   
 [Função Object. getprototypeof](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [Constante undefined](../../javascript/reference/undefined-constant-javascript.md)   
 [Operadores de comparação](../../javascript/reference/comparison-operators-javascript.md)   
 [Tipos de Dados](../../javascript/data-types-javascript.md)   
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)