---
title: "Operador de atribuição de adição (+ =) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: +=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- addition assignment operator (+=)
- += operator
- assignment operators, JavaScript
ms.assetid: 8517d05c-38b0-4107-bea4-253eb420f438
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38d86c537dda90dd7f44923b97384b3609dad5ba
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="addition-assignment-operator--javascript"></a>Operador de atribuição de adição (+=) (JavaScript)
Adiciona o valor de uma expressão ao valor de uma variável e atribui o resultado à variável.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result += expression   
```  
  
## <a name="parameters"></a>Parâmetros  
 `result`  
 Qualquer variável.  
  
 `expression`  
 Qualquer expressão.  
  
## <a name="remarks"></a>Comentários  
 Usar esse operador é exatamente o mesmo que especificar: `result = result + expression`.  
  
 Os tipos de duas expressões determinam o comportamento do `+=` operador.  
  
|If|Then|  
|--------|----------|  
|As duas expressões são numéricos ou booleanos|Adicionar|  
|As duas expressões são cadeias de caracteres|Concatenar|  
|Uma expressão é numérica e a outra é uma cadeia de caracteres|Concatenar|  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador de adição (+)](../../javascript/reference/addition-operator-decrement-javascript.md)   
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)