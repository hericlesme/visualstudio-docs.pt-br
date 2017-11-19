---
title: Operadores de decremento (-) (JavaScript) e de incremento (+ +) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- --
- ++
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- increment operators, syntax
- ++ operator
- ++ operator, about ++ operator
- decrement operators, syntax
- -- operator
ms.assetid: 49eaf4cf-8818-478d-a429-cdd2ece20811
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 806bd321bb1f81d585a6595b8cf2842571164921
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="increment--and-decrement----operators-javascript"></a>Operadores de incremento (++) e de decremento (--) (JavaScript)
Os incrementos de operador de incremento e diminui de operador de decremento o valor de uma variável por um.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
      result = ++variable  
result = --variable  
result = variable++  
result = variable--  
```  
  
## <a name="parameters"></a>Parâmetros  
 `result`  
 Qualquer variável.  
  
 `variable`  
 Qualquer variável.  
  
## <a name="remarks"></a>Comentários  
 Se o operador aparecer antes da variável, o valor é modificado antes da expressão é avaliada. Se o operador aparecer depois da variável, o valor é modificado depois que a expressão é avaliada.  Em outras palavras, considerando `j = ++k;`, o valor de `j` é o valor original da `k` mais um; considerando `j = k++;`, o valor de `j` é o valor original da `k`, que é incrementado depois que seu valor é atribuído a `j`.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)