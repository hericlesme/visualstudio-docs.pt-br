---
title: "Operador de atribuição Right Shift sem sinal (&gt;&gt;&gt;=) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '>>>='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>>>= operator'
- unsigned right shift assignment operator (>>>=)
- assignment operators, JavaScript
ms.assetid: f67c3737-7d39-41ae-9c11-8b16d38f6179
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1272cbb58645df605743c6790642cd0e295442aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="unsigned-right-shift-assignment-operator-gtgtgt-javascript"></a>Operador de atribuição Right Shift sem sinal (&gt;&gt;&gt;=) (JavaScript)
Desloca para a direita o valor de uma variável o número de bits especificado pelo valor de uma expressão, sem manter o sinal, e atribui o resultado à variável.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result >>>= expression  
```  
  
## <a name="parameters"></a>Parâmetros  
 *resultado*  
 Qualquer variável.  
  
 *expressão*  
 Qualquer expressão.  
  
## <a name="remarks"></a>Comentários  
 Usando o >>> = operador é exatamente o mesmo que fazer o seguinte:  
  
```JavaScript  
result = result >>> expression  
```  
  
 O  **>>>=**  operador desloca os bits de *resultados* direita pelo número de bits especificado *expressão*. Zeros são preenchidos da esquerda. Dígitos deslocados à direita são descartados. Por exemplo:  
  
```JavaScript  
var temp  
temp = -14  
temp >>>= 2  
```  
  
 A variável *temp* tem um valor inicial de -14 (11111111 11111111 11111111 11110010 em binário de complemento de dois). Quando alterado direita dois bits, o valor é igual a 1073741820 (00111111 11111111 11111111 11111100 em binário).  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador Right Shift sem sinal (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Bit a bit operador Left Shift (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operador de deslocamento para a direita bit a bit (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)