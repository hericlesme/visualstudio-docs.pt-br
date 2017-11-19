---
title: Resto operador (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '%'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- remainder operator, JavaScript
- '% operator [JavaScript]'
- Remainder function [JavaScript]
ms.assetid: 087d654f-623b-498d-95ff-596d26bf674d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce74b8512b25cfe215d294873102b274623b42a2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="remainder-operator-javascript"></a>Operador restante (JavaScript)
Divide o valor de uma expressão, o valor de outra e retorna o resto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result = number1 % number2  
```  
  
## <a name="arguments"></a>Arguments  
 `result`  
 Qualquer variável.  
  
 `number1`  
 Qualquer expressão numérica.  
  
 `number2`  
 Qualquer expressão numérica.  
  
## <a name="remarks"></a>Comentários  
 O operador restante divide `number1` por `number2`e retorna somente o resto como `result`. O sinal de `result` é o mesmo que o sinal de `number1`. O valor de `result` está entre 0 e o valor absoluto de `number2`.  
  
 O código a seguir mostra como usar o operador restante.  
  
```  
var modResult = 19 % 6.7;  
document.write(modResult);  
  
// Output: 5.6  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)
