---
title: "Função isNaN (JavaScript) | Microsoft Docs"
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
- isNaN
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- isNaN method
ms.assetid: 5af4eb29-72f6-484f-93bd-04ae1261f849
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b7e6d3687e795ea5d5e38308a8af0d73ba7f5ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="isnan-function-javascript"></a>Função isNaN (JavaScript)
Retorna um valor booliano que indica se um valor é o valor reservado `NaN` (e não um número).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
isNaN(numValue)   
```  
  
## <a name="return-value"></a>Valor de retorno  
 `true` se o valor convertido para o tipo `Number` for o `NaN`. Caso contrário, `false`.  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `numValue` é o valor a ser testado com `NaN`.  
  
 Você normalmente usa esse método para testar valores retornados dos métodos `parseInt` e `parseFloat`.  
  
 Como alternativa, uma variável que contém `NaN` ou outro valor pode ser comparado a mesmo. Se ele se compara como diferente, é `NaN`. Isso ocorre porque `NaN` é o único valor que não é igual a mesmo.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto Global](../../javascript/reference/global-object-javascript.md)  
  
## <a name="example"></a>Exemplo  
  
```JavaScript  
// Returns false.  
isNaN(100);  
  
// Returns false.  
isNaN("100");  
  
// Returns true.  
isNaN("ABC");  
  
// Returns true.  
isNaN("10C");  
  
// Returns true.  
isNaN("abc123");  
  
// Returns true.  
isNaN(Math.sqrt(-1));           
```  
  
## <a name="see-also"></a>Consulte também  
 [Função isFinite](../../javascript/reference/isfinite-function-javascript.md)   
 [Constante NaN](../../javascript/reference/nan-constant-javascript.md)   
 [Função parseFloat](../../javascript/reference/parsefloat-function-javascript.md)   
 [Função parseInt](../../javascript/reference/parseint-function-javascript.md)