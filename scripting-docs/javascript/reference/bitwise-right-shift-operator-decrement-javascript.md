---
title: Operador de deslocamento para a direita bit a bit (&gt;&gt;) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '>>'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>> operator'
- '>> operator, about >> operator'
- '>> operator, bitsets'
- bitwise operators, right shift operator
ms.assetid: 89dc57e0-0b0d-49a4-a8ed-56d8bb20f3e3
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70db0c176b475886a26cfe4c06f7f2f0c9d4fc2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-right-shift-operator-gtgt-javascript"></a>Operador de deslocamento para a direita bit a bit (&gt;&gt;) (JavaScript)
Direita desloca os bits de uma expressão, mantendo o sinal.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result = expression1 >> expression2  
```  
  
## <a name="parameters"></a>Parâmetros  
 *resultado*  
 Qualquer variável.  
  
 *Expression1*  
 Qualquer expressão.  
  
 *Expression2*  
 Qualquer expressão.  
  
## <a name="remarks"></a>Comentários  
 O >> operador desloca os bits de *expression1* direita pelo número de bits especificado *expression2*. O sinal de bits de *expression1* é usado para preencher os dígitos da esquerda. Dígitos deslocados à direita são descartados. Por exemplo, depois que o código a seguir é avaliado, *temp* tem um valor de -4:-14 (binário do complemento do 11110010 em dois) deslocada à direita dois bits é igual a -4 (binário do complemento do 11111100 em dois).  
  
```JavaScript  
var temp  
temp = -14 >> 2  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Bit a bit operador Left Shift (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operador de atribuição de Shift direita (>> =)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)   
 [Operador Right Shift sem sinal (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)