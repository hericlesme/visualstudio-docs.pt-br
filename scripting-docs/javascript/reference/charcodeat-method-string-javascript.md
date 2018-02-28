---
title: "Método charCodeAt (String) (JavaScript) | Microsoft Docs"
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
- charCodeAt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- charCodeAt method
ms.assetid: 5b0290a7-ee4d-4738-a909-c02ef64a2f1a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e7b8e62dfd29aa42d9816d0c5e27cc90440751a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="charcodeat-method-string-javascript"></a>Método charCodeAt (String) (JavaScript)
Retorna o valor Unicode do caractere no local especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
strObj. charCodeAt(index)  
```  
  
## <a name="parameters"></a>Parâmetros  
 `strObj`  
 Necessário. Qualquer `String` literal de cadeia de caracteres ou objeto.  
  
 `index`  
 Necessário. O índice de base zero do caractere desejado. Se não houver nenhum caractere no índice especificado, `NaN` será retornado.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `charCodeAt`.  
  
```JavaScript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";   
document.write(str.charCodeAt(str.length - 1));  
  
// Output: 90   
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função String.fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)