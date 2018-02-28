---
title: "Função isFinite (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- isFinite
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- finite numbers
- isFinite method
ms.assetid: ea9287d2-892f-496b-86b7-f9196868d5cf
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce78afe59190a03fb079841e7691f84c01eebedd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="isfinite-function-javascript"></a>Função isFinite (JavaScript)
Determina se um número fornecido é finito.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
isFinite(number)   
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `number` argumento é qualquer valor numérico.  
  
 O `isFinite` função retorna `true` se `number` for qualquer valor diferente de `NaN`, infinito negativo ou infinidade positiva. Nos três casos, ele retorna **false**.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto Global](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Função isNaN](../../javascript/reference/isnan-function-javascript.md)