---
title: Operador de atribuição XOR bit a bit (^ =) (JavaScript) | Microsoft Docs
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
- ^=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ^= operator, about ^= operator
- assignment operators, bitwise [JavaScript]
- bitwise operators, XOR operator
- XOR operator
- ^= operator
ms.assetid: a6ded216-27b6-4fc4-a51b-7d10cc6f820c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 511ff5b3346bb2b04bf4c24cb3e0b715b2ccf4c5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634026"
---
# <a name="bitwise-xor-assignment-operator--javascript"></a>Operador de atribuição AND bit a bit (^=) (JavaScript)
Executa um OR exclusivo bit a bit em uma variável e uma expressão e atribui o resultado à variável.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result ^= expression  
```  
  
## <a name="parameters"></a>Parâmetros  
 *resultado*  
 Qualquer variável.  
  
 *expressão*  
 Qualquer expressão.  
  
## <a name="remarks"></a>Comentários  
 Usando o  **^=**  operador é exatamente o mesmo que especificar:  
  
```JavaScript  
result = result ^ expression  
```  
  
 O  **^=**  operador examina a representação binária dos valores de duas expressões e faz uma operação OR exclusiva bit a bit neles. O resultado dessa operação se comporta da seguinte maneira:  
  
```JavaScript  
0101    (result)  
1100    (expression)  
----  
1001    (result)  
```  
  
 Quando uma e apenas uma das expressões tem um 1 em um dígito, o resultado tem um 1 nesse dígito. Caso contrário, o resultado tem um 0 nesse dígito.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador XOR bit a bit (^)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)   
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)