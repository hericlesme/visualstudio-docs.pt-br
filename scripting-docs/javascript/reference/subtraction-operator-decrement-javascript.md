---
title: Operador de subtração (-) (JavaScript) | Microsoft Docs
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
- '-'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '- operator, about - operator'
- '- operator'
- negation operator
- subtraction operator, syntax
- arithmetic operators, subtraction
- operators, subtraction
ms.assetid: cd0681d3-15cd-49fe-b4dd-e087de55d778
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb79aab0a57c733871dbfc73ac96c7ddbf4db37c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640646"
---
# <a name="subtraction-operator---javascript"></a>Operador de subtração (-) (JavaScript)
Subtrai o valor de uma expressão de outra ou fornece negação unário de uma única expressão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result = number1 - number2;  
```  
  
## <a name="parameters"></a>Parâmetros  
 *resultado*  
 Qualquer variável numérica.  
  
 `number`  
 Qualquer expressão numérica.  
  
 `number1`  
 Qualquer expressão numérica.  
  
 `number2`  
 Qualquer expressão numérica.  
  
## <a name="remarks"></a>Comentários  
 Na sintaxe 1, o  **-**  operador é o operador de subtração aritmético usado para localizar a diferença entre dois números. Na sintaxe 2, o  **-**  operador é usado como o operador de negação unário para indicar o valor negativo de uma expressão.  
  
 Para a sintaxe 2, para todos os operadores unários, as expressões são avaliadas da seguinte maneira:  
  
-   Se aplicado a indefinido ou `null` expressões, um erro de tempo de execução é gerado.  
  
-   Os objetos são convertidos em cadeias de caracteres.  
  
-   Cadeias de caracteres são convertidas em números, se possível. Caso contrário, será gerado um erro de tempo de execução.  
  
-   Valores boolianos são tratados como números (0 se for false, 1 se for true).  
  
 O operador é aplicado para o número resultante. Na sintaxe 2, se o número resultante é diferente de zero, *resultados* é igual ao número resultante com o sinal revertido. Se o número resultante for zero, *resultados* é zero.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador de atribuição de subtração (-)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)   
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)