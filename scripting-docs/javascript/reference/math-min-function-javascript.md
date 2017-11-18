---
title: "Função Math.min (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: min
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: min method
ms.assetid: a1d7dd85-27ef-45cd-aa2a-f8e80f0b2898
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb496cff65db11cf6c99d6a6e687f39e20ea857c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="mathmin-function-javascript"></a>Função Math.min (JavaScript)
Retorna o menor de um conjunto de expressões numéricas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Math.min([number1[, number2[... [,numberN]]]])  
```  
  
## <a name="remarks"></a>Comentários  
 Opcional `number1, number2, ..., numberN` argumentos são expressões numéricas a ser avaliada.  
  
 Se nenhum argumento for fornecido, o valor de retorno é igual a [Number. positive_infinity](../../javascript/reference/number-constants-javascript.md). Se qualquer argumento for `NaN`, o valor retornado também é `NaN`.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como obter a menor das duas expressões.  
  
```JavaScript  
var x = Math.min(107 - 3, 48 * 90);  
document.write(x);  
  
// Output:  
// 104  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função Math.max](../../javascript/reference/math-max-function-javascript.md)