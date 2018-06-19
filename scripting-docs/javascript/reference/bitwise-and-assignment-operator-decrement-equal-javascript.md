---
title: Operador de atribuição AND bit a bit (&amp;=) (JavaScript) | Microsoft Docs
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
- '&='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '&= operator'
- assignment operators, bitwise [JavaScript]
- AND operator
- bitwise operators, AND operator
ms.assetid: e7e2eabb-4fc1-4fdc-9dd8-1e6d715371fa
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dfd2a77e66296cafc6c8403570f0536e1333e081
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634036"
---
# <a name="bitwise-and-assignment-operator-amp-javascript"></a>Operador de atribuição AND bit a bit (&amp;=) (JavaScript)
Define o resultado de uma operação AND de bit a bit no valor de uma variável e o valor de uma expressão. A variável e a expressão são tratados como inteiros de 32 bits.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result &= expression  
```  
  
## <a name="parameters"></a>Parâmetros  
 `result`  
 Qualquer variável.  
  
 `expression`  
 Qualquer expressão.  
  
## <a name="remarks"></a>Comentários  
 Usar esse operador é o mesmo que especificar:  
  
```JavaScript  
result = result & expression  
```  
  
 O [operador e bit a bit (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md) examina a representação binária dos valores de `result` e `expression` e faz uma operação AND de bit a bit neles. A saída dessa operação se comporta assim:  
  
```JavaScript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
expr1 &= expr2;  
  
document.write(expr1);  
```  
  
 Sempre que as duas expressões tiverem um 1 em um dígito, o resultado tem um 1 nesse dígito. Caso contrário, o resultado tem um 0 nesse dígito.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador AND bit a bit (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)   
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)