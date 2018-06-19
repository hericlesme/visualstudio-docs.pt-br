---
title: Operador de vírgula (,) (JavaScript) | Microsoft Docs
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
- '%2C'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comma operator
ms.assetid: 699fa0bf-cd0a-45ee-a291-2fbed4ecd470
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cb504beefc5ce4c260ec8296e2cf097e17d349e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634176"
---
# <a name="comma-operator--javascript"></a>Operador de vírgula (,) (JavaScript)
Faz com que duas expressões sejam executadas consecutivamente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
expression1, expression2  
```  
  
## <a name="parameters"></a>Parâmetros  
 `expression1`  
 Qualquer expressão.  
  
 `expression2`  
 Qualquer expressão.  
  
## <a name="remarks"></a>Comentários  
 O `,` operador faz com que as expressões a serem executados na ordem da esquerda para a direita. Um uso comum para o `,` operador está na expressão de incremento de uma `for` loop. Por exemplo:  
  
```JavaScript  
j=25;  
for (i = 0; i < 10; i++, j++)  
{  
   k = i + j;  
}  
```  
  
 O `for` instrução permite apenas uma única expressão ser executado no final de cada um loop de passagem. O `,` operador permite que várias expressões a serem tratados como uma única expressão, para que as duas variáveis podem ser incrementadas.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução for](../../javascript/reference/for-statement-javascript.md)   
 [Precedência do operador](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumo de operador (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)