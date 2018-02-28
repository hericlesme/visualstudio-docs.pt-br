---
title: "Operadores de comparação (JavaScript) | Microsoft Docs"
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
- Comparison
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comparison operators, script
- greater than operator
- comparison operators
- greater than or equal to operator
- inequity operator
- identity operator
ms.assetid: 084f90f0-d010-47cf-96dd-13d637fc9b68
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 067d570523fc2241b4f2e0442785a49aedb15200
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="comparison-operators-javascript"></a>Operadores de comparação (JavaScript)
Retorna um valor booliano que indica o resultado da comparação.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
expression1 comparisonoperator expression2  
```  
  
## <a name="parameters"></a>Parâmetros  
 `expression1`  
 Qualquer expressão.  
  
 `comparisonoperator`  
 Qualquer operador de comparação.  
  
 `expression2`  
 Qualquer expressão.  
  
## <a name="remarks"></a>Comentários  
 Ao comparar cadeias de caracteres, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] usa o valor do caractere Unicode da expressão de cadeia de caracteres.  
  
 A seguir descreve como os grupos diferentes de operadores se comportam dependendo dos tipos e valores de `expression1` e `expression2`:  
  
 Operadores relacionais: `<`, `>`, `<=`,`>=`  
  
-   Tente converter ambos `expression1` e `expression2` em números.  
  
-   Se as duas expressões são cadeias de caracteres, fazer uma comparação de cadeia de caracteres.  
  
-   Se qualquer expressão for `NaN`, retorne `false`.  
  
-   Zero negativo é igual a zero positivo.  
  
-   Infinito negativo é menor que tudo, incluindo ele mesmo.  
  
-   Infinito positivo é maior que tudo, incluindo ele mesmo.  
  
 Operadores de igualdade: `==`,`!=`  
  
-   Se os tipos das duas expressões são diferentes, tente convertê-los em uma cadeia de caracteres, número ou booleano.  
  
-   `NaN`não é igual a qualquer coisa, incluindo ele mesmo.  
  
-   Zero negativo é igual a zero positivo.  
  
-   `null`é igual a ambos `null` e `undefined`.  
  
-   Os valores são considerados iguais se forem idênticas cadeias de caracteres, números numericamente equivalentes, o mesmo objeto, idênticos valores booleanos, ou (se tipos diferentes) podem ser forçados em uma dessas situações.  
  
-   Cada outra comparação é considerada diferente.  
  
 Operadores de identidade: `===`,`!==`  
  
 Esses operadores se comportam da mesma maneira como os operadores de igualdade, exceto que não é feita nenhuma conversão de tipo. Se os tipos de ambas as expressões não forem iguais, essas expressões sempre retornam `false`.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)