---
title: "Função Math Round (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: round
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Round method
- Math object
ms.assetid: 51008df3-5d0c-4951-84cb-4f41000db0be
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9543d529e3d0e4e45cff29f1286edbfad8dc0e27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="mathround-function-javascript"></a>Função Math.round (JavaScript)
Retorna uma expressão numérica fornecida, arredondada para o inteiro mais próximo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Math.round(  
number  
)   
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `number` argumento é o valor a ser arredondado para o inteiro mais próximo.  
  
 Para números positivos, se a parte decimal do `number` é 0,5 ou maior, o valor de retorno é igual para o menor inteiro maior que `number`. Se a parte decimal é inferior a 0,5, o valor de retorno é o maior inteiro menor ou igual a `number`.  
  
 Para números negativos, se a parte decimal é exatamente -0,5, o valor de retorno é o menor inteiro maior que o número.  
  
 Por exemplo, `Math.round(8.5)` retorna 9, mas `Math.round(-8.5)` retorna -8.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto Math](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Função Math.random](../../javascript/reference/math-random-function-javascript.md)