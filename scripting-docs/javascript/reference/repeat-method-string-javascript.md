---
title: "Método repeat (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: fe02cdfd-f0f6-45a2-ad36-31c4300ef142
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1a3d6edce877a97b0e46a69c43b667231c26981
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="repeat-method-string-javascript"></a>Método repeat (String) (JavaScript)
Retorna que um novo objeto de cadeia de caracteres com um valor igual à cadeia de caracteres original repetido o número de vezes especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
stringObj.repeat(count);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `stringObj`  
 Necessário. O objeto de cadeia de caracteres.  
  
 `count`  
 Necessário. O número de vezes a repetir a cadeia de caracteres original na cadeia de caracteres retornada.  
  
## <a name="exceptions"></a>Exceções  
 Este método lança um RangeError se e somente se o argumento for negativo ou +Infinity.  
  
## <a name="remarks"></a>Comentários  
 O método `repeat` concatena a cadeia de caracteres original à nova cadeia de caracteres o número de vezes especificado por `count`.  
  
 Este método gera um erro se `count` não for um número positivo menor que `Infinity`.  
  
## <a name="example"></a>Exemplo  
  
```JavaScript  
"abc".repeat(3); // Returns "abcabcabc"  
"abc".repeat(0); // Returns an empty string.  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]