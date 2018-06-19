---
title: Operador XOR bit a bit (^) (JavaScript) | Microsoft Docs
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
- ^
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- bitwise operators, XOR operator
- XOR operator
ms.assetid: 44ef0d18-abb5-4d83-9e77-6394635b3f48
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ebe8ff9805793bf306688622b0b29007b1562e2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633846"
---
# <a name="bitwise-xor-operator--javascript"></a>Operador XOR bit a bit (^) (JavaScript)
Executa um OR exclusivo bit a bit em duas expressões.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result = expression1 ^ expression2  
```  
  
## <a name="parameters"></a>Parâmetros  
 *resultado*  
 Qualquer variável.  
  
 *Expression1*  
 Qualquer expressão.  
  
 *Expression2*  
 Qualquer expressão.  
  
## <a name="remarks"></a>Comentários  
 O  **^**  operador examina a representação binária dos valores de duas expressões e faz uma operação OR exclusiva bit a bit neles. O resultado dessa operação se comporta da seguinte maneira:  
  
```JavaScript  
0101   (expression1)  
1100   (expression2)  
----  
1001   (result)  
```  
  
 Quando uma e apenas uma das expressões tem um 1 em um dígito, o resultado tem um 1 nesse dígito. Caso contrário, o resultado tem um 0 nesse dígito.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador de atribuição XOR bit a bit (^ =)](../../javascript/reference/bitwise-xor-assignment-operator-decrement-hat-equal-javascript.md)   
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)