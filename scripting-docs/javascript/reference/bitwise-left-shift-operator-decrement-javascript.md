---
title: Bit a bit operador Left Shift (&lt;&lt;) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: <<
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- << operator
- left shift operators
- << operator, about << operator
- bitwise operators, Left Shift operator
ms.assetid: 18148596-7b86-4add-aeef-106991c69435
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d63fc50659695f518e581edbed67c009b36577f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-left-shift-operator-ltlt-javascript"></a>Bit a bit operador Left Shift (&lt;&lt;) (JavaScript)
Esquerda desloca os bits de uma expressão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result = expression1 << expression2  
```  
  
## <a name="parameters"></a>Parâmetros  
 *resultado*  
 Qualquer variável.  
  
 *Expression1*  
 Qualquer expressão.  
  
 *Expression2*  
 Qualquer expressão.  
  
## <a name="remarks"></a>Comentários  
 O  **<<**  operador desloca os bits de *expression1* esquerda pelo número de bits especificado *expression2*. Por exemplo:  
  
```JavaScript  
var temp  
temp = 14 << 2  
```  
  
 A variável *temp* tem um valor de 56 porque 14 (00001110 em binário) adiantadas dois bits esquerdo for igual a 56 (00111000 em binário).  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador Left Shift atribuição (<\<=)](../../javascript/reference/left-shift-assignment-operator-decrement-equal-javascript.md)   
 [Operador de deslocamento para a direita bit a bit (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Operador Right Shift sem sinal (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)