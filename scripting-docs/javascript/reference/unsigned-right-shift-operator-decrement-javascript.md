---
title: Operador Right Shift sem sinal (&gt;&gt;&gt;) (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '>>>'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- unsigned right shift operator (>>>)
- '>>> operator'
ms.assetid: df48bdfc-8741-46ab-b681-449da57ac95c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efb873bedc0a64089c7ec892d6378b4869c0ca21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641636"
---
# <a name="unsigned-right-shift-operator-gtgtgt-javascript"></a>Operador Right Shift sem sinal (&gt;&gt;&gt;) (JavaScript)
Direita desloca os bits de uma expressão, sem manter o sinal.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result = expression1 >>> expression2  
```  
  
## <a name="parameters"></a>Parâmetros  
 *resultado*  
 Qualquer variável.  
  
 *Expression1*  
 Qualquer expressão.  
  
 *Expression2*  
 Qualquer expressão.  
  
## <a name="remarks"></a>Comentários  
 O  **>>>**  operador desloca os bits de *expression1* direita pelo número de bits especificado *expression2*. Zeros são preenchidos da esquerda. Dígitos deslocados à direita são descartados. Por exemplo:  
  
```JavaScript  
var temp  
temp = -14 >>> 2  
```  
  
 A variável *temp* tem um valor inicial -14 (11111111 11111111 11111111 11110010 em binário de complemento de dois). Quando é deslocada à direita dois bits, o valor é igual a 1073741820 (00111111 11111111 11111111 11111100 em binário).  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador de atribuição Right Shift sem sinal (>>> =)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)   
 [Bit a bit operador Left Shift (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operador de deslocamento para a direita bit a bit (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)