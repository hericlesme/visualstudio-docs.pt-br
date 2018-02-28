---
title: "Lógica operador NOT (!) (JavaScript) | Microsoft Docs"
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
- '!'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Logical NOT operator
- '! operator'
- '! operator, about ! operator'
ms.assetid: 68c3dc71-ae95-4293-9155-67405846d71d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29c27b9cd670989eb2112de5067e68bd09d76903
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="logical-not-operator--javascript"></a>Operador NOT lógico (!) (JavaScript)
Executa uma negação lógica em uma expressão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result = !expression  
```  
  
## <a name="parameters"></a>Parâmetros  
 *resultado*  
 Qualquer variável.  
  
 *expressão*  
 Qualquer expressão.  
  
## <a name="remarks"></a>Comentários  
 A tabela a seguir ilustra como *resultados* é determinado.  
  
|Se `expression` é|Em seguida, `result` é|  
|------------------------|----------------------|  
|verdadeiro|False|  
|False|verdadeiro|  
  
 Todos os operadores unários, como o **!** operador, avalie expressões da seguinte maneira:  
  
-   Se aplicado a indefinido ou `null` expressões, um erro de tempo de execução é gerado.  
  
-   Os objetos são convertidos em cadeias de caracteres.  
  
-   Cadeias de caracteres são convertidas em números, se possível. Caso contrário, será gerado um erro de tempo de execução.  
  
-   Valores boolianos são tratados como números (0 se for false, 1 se for true).  
  
 O operador é aplicado para o número resultante.  
  
 Para o **!** operador, se *expressão* é diferente de zero, *resultados* é zero. Se *expressão* for zero, *resultados* é 1.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Bit a bit operador (~)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)   
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)