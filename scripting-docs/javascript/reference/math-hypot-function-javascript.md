---
title: "Função Math hypot (JavaScript) | Microsoft Docs"
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
ms.assetid: 31488f5a-2230-4114-911e-b6d854c7b0a0
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a66c0b082356b8dde3f51f739c130378d694f3b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="mathhypot-function-javascript"></a>Função math.hypot (JavaScript)
Retorna a raiz quadrada da soma dos quadrados dos argumentos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Math.hypot ( value1[, value2[, ...values] );  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `value1`  
 Necessário. O primeiro número.  
  
 `value2`  
 Opcional. O segundo número.  
  
 `values`  
 Opcional. Um ou mais números.  
  
## <a name="remarks"></a>Comentários  
 Se qualquer argumento for NaN, a função retorna NaN. Não nenhum argumento for fornecido, a função retorna 0.  
  
## <a name="example"></a>Exemplo  
 O seguinte exemplo mostra como usar a função `Math.hypot`.  
  
```JavaScript  
Math.hypot(3, 4);  
// Returns 5  
  
Math.hypot(3, "4");  
// Returns 5  
  
Math.hypot(3, "four");  
// Returns NaN   
  
Math.hypot(3, 4, 10);  
// Returns 11.180339887498949  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]