---
title: "Função Math clz32 (JavaScript) | Microsoft Docs"
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
ms.assetid: 34615d7a-6d88-4ab5-a696-7e496caa51db
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 511f407acc327a32ed6c53c12283503e20b514fe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="mathclz32-function-javascript"></a>Função Math.clz32 (JavaScript)
Retorna o número de bits zero à esquerda na representação binária de 32 bits de um número.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
Math.clz32(  
number  
)   
```  
  
## <a name="remarks"></a>Comentários  
 Se `number` for 0, o resultado será 32. Se o bit mais significativo da codificação binária de 32 bits do `number` for 1, o resultado será 0.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **Aplica-se a**: [objeto Math](../../javascript/reference/math-object-javascript.md)