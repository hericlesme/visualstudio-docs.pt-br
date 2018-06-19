---
title: Função ACOS (JavaScript) | Microsoft Docs
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
- acos
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- acos method
- arcosine method
ms.assetid: 828cb3c3-bdf7-4bb7-97ae-3617ce4b2d62
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 773499287e215fbc161f289954811d3ef62bcba6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638336"
---
# <a name="mathacos-function-javascript"></a>Função Math.acos (JavaScript)
Retorna o arco cosseno (ou o cosseno inverso) de um número.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Math.acos(number)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 O argumento `number` necessário é uma expressão numérica.  
  
## <a name="return-value"></a>Valor de retorno  
 O arco cosseno de `number` argumento, em radianos.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como usar a função `acos`.  
  
```JavaScript  
var v1 = Math.acos(-1.0);  
var v2 = Math.cos(-1.0);  
  
document.write(v1);  
document.write("<br/>");  
document.write(v2);  
  
// Output:  
// 3.141592653589793  
// 0.5403023058681398  
  
```  
  
## <a name="remarks"></a>Comentários  
 **Aplica-se a**: [objeto Math](../../javascript/reference/math-object-javascript.md)  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função ASIN](../../javascript/reference/math-asin-function-javascript.md)   
 [Função ATAN](../../javascript/reference/math-atan-function-javascript.md)   
 [Função Math.CoS](../../javascript/reference/math-cos-function-javascript.md)   
 [Função Sin](../../javascript/reference/math-sin-function-javascript.md)   
 [Função Math.tan](../../javascript/reference/math-tan-function-javascript.md)   
 [Objeto Math](../../javascript/reference/math-object-javascript.md)