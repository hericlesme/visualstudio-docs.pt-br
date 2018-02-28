---
title: "Operador de atribuição de Shift direita (&gt;&gt;=) (JavaScript) | Microsoft Docs"
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
- '>>='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>>= operator [JavaScript]'
- right shift operators [JavaScript]
- assignment operators, JavaScript
ms.assetid: 8c1f7f90-e3ac-42ee-94f2-5ccc47d7aef6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb93d146ad00bd19c09fb4cfca3af776a11f245d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="right-shift-assignment-operator-gtgt-javascript"></a>Operador de atribuição de Shift direita (&gt;&gt;=) (JavaScript)
Desloca para a direita o valor de uma variável o número de bits especificado pelo valor de uma expressão, mantendo o sinal, e atribui o resultado à variável.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result >>= expression  
```  
  
## <a name="parameters"></a>Parâmetros  
 *resultado*  
 Qualquer variável.  
  
 *expressão*  
 Qualquer expressão.  
  
## <a name="remarks"></a>Comentários  
 Usando o  **>>=**  operador é exatamente o mesmo que especificar:  
  
```JavaScript  
result = result >> expression  
```  
  
 O  **>>=**  operador desloca os bits de *resultados* direita pelo número de bits especificado *expressão*. O sinal de bits de *resultados* é usado para preencher os dígitos da esquerda. Dígitos deslocados à direita são descartados. Por exemplo, depois que o código a seguir é avaliado, *temp* tem um valor de -4: 14 (11110010 em binário) deslocada à direita dois bits é igual a -4 (11111100 em binário).  
  
```JavaScript  
var temp  
temp = -14  
temp >>= 2  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Bit a bit operador Left Shift (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [Operador de deslocamento para a direita bit a bit (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [Operador Right Shift sem sinal (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)