---
title: "Método valueOf (booliano) | Microsoft Docs"
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
ms.assetid: ac6ad343-7663-406a-a2b7-4cc5025ca3d6
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c36eda63fb38886df4d8bffec7cfdbb6c6d05eb8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="valueof-method-boolean"></a>Método valueOf (booliano)
Retorna o valor primitivo do booliano especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
boolean.valueOf()  
```  
  
## <a name="return-value"></a>Valor de retorno  
 O valor primitivo (true ou false) de booliano.  
  
## <a name="remarks"></a>Comentários  
 O código a seguir mostra como usar esse método.  
  
```JavaScript  
var bool = new Boolean("true");  
var s = bool.valueOf();  
document.write(s);  
  
// Output: true  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]