---
title: "Função ACOSH (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 881dd2a0-36a5-403b-a3dc-523d8e1e1317
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1fd75140dfcf3d9ac703c2aeadf68bea4da9e0dc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="mathacosh-function-javascript"></a>Função Math.acosh (JavaScript)
Retorna o arco cosseno hiperbólico (ou o cosseno hiperbólico inverso) de um número.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Math.acosh(number)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 O argumento `number` necessário é uma expressão numérica.  
  
## <a name="return-value"></a>Valor de retorno  
 O cosseno hiperbólico inverso do argumento `number`, em radianos.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como usar a função `acosh`.  
  
```JavaScript  
var v1 = Math.acosh(3);  
vary v2 = Math.acosh(-1);  
  
document.write(v1);  
document.write("</br>");  
document.write(v2);  
  
// Output:  
// 1.762747174039086  
// NaN  
  
```  
  
## <a name="remarks"></a>Comentários  
 **Aplica-se a**: [objeto Math](../../javascript/reference/math-object-javascript.md)  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função ACOS](../../javascript/reference/math-acos-function-javascript.md)   
 [Função ASIN](../../javascript/reference/math-asin-function-javascript.md)   
 [Função ATAN](../../javascript/reference/math-atan-function-javascript.md)   
 [Função Math.CoS](../../javascript/reference/math-cos-function-javascript.md)   
 [Função Sin](../../javascript/reference/math-sin-function-javascript.md)   
 [Função Math.tan](../../javascript/reference/math-tan-function-javascript.md)   
 [Objeto Math](../../javascript/reference/math-object-javascript.md)