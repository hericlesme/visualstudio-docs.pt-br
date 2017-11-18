---
title: "Função Math.Max (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: max
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: max method
ms.assetid: f3ea1b8a-5fd0-482a-971b-b7f8e2b9b7eb
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adf66164346f3802d92f8e0de82356df49bad5fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="mathmax-function-javascript"></a>Função Math.max (JavaScript)
Retorna o maior de um conjunto de expressões numéricas fornecidas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Math.max([number1[, number2[... [, numberN]]]])   
```  
  
## <a name="remarks"></a>Comentários  
 Opcional `number1, number2, ..., numberN` argumentos são expressões numéricas a ser avaliada.  
  
 Se nenhum argumento for fornecido, o valor de retorno é igual a [Number. negative_infinity](../../javascript/reference/number-constants-javascript.md). Se qualquer argumento for `NaN`, o valor retornado também é `NaN`.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como obter maior de duas expressões.  
  
```JavaScript  
var x = Math.max(107 - 3,  48 * 90);  
document.write(x);  
  
// Output:  
// 4320  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função Math.min](../../javascript/reference/math-min-function-javascript.md)