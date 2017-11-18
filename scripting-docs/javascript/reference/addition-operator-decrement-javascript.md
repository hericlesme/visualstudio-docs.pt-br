---
title: "Operador de adição (+) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: +
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arithmetic operators, addition
- strings [Visual Studio], concatenating
- concatenation operators, vs. addition operator
- addition operator
- + operator
ms.assetid: ec1237d3-e78b-4e77-bd7d-c0204cf03acd
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70ff02b1f234da7b88d28e66da82262ccef7bfaf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="addition-operator--javascript"></a>Operador de adição (+) (JavaScript)
Adiciona o valor de uma expressão numérica para outro ou concatena duas cadeias de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result = expression1 + expression2  
```  
  
## <a name="parameters"></a>Parâmetros  
 `result`  
 Qualquer variável.  
  
 `expression1`  
 Qualquer expressão.  
  
 `expression2`  
 Qualquer expressão.  
  
## <a name="remarks"></a>Comentários  
 Os tipos de duas expressões determinam o comportamento do  **+**  operador.  
  
|If|Then|  
|--------|----------|  
|As duas expressões são numéricos ou booleanos|Adicionar|  
|As duas expressões são cadeias de caracteres|Concatenar|  
|Uma expressão é numérica e a outra é uma cadeia de caracteres|Concatenar|  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador de atribuição de adição (+ =)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)   
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)