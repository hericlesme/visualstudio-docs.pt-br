---
title: "Bit a bit ou operador de atribuição (| =) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '|='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- assignment operators, bitwise [JavaScript]
- '|= operator'
- bitwise operators, OR operator
- OR operator
ms.assetid: 9b424ff6-4442-4621-b3b6-83e7fd1e5cd5
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ce9cadcf07906c9eba6749706620ae6293c2682
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-or-assignment-operator--javascript"></a>Operador de atribuição OR bit a bit (|=) (JavaScript)
Executa um OR bit a bit no valor de uma variável e no valor de uma expressão e atribui o resultado à variável.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result |= expression  
```  
  
## <a name="parameters"></a>Parâmetros  
 *resultado*  
 Qualquer variável.  
  
 *expressão*  
 Qualquer expressão.  
  
## <a name="remarks"></a>Comentários  
 Usar esse operador é exatamente o mesmo que especificar:  
  
```JavaScript  
result = result | expression  
```  
  
 O **&#124; =** operador examina a representação binária dos valores de *resultados* e *expressão* e faz uma operação OR bit a bit neles. O resultado dessa operação se comporta assim:  
  
```JavaScript  
0101    (result)  
1100    (expression)  
----  
1101    (output)  
```  
  
 Sempre que qualquer uma das expressões tem um 1 em um dígito, o resultado tem um 1 nesse dígito. Caso contrário, o resultado tem um 0 nesse dígito.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [OR bit a bit operador (&#124;)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)   
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)