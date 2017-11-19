---
title: "Método (String) (JavaScript) codePointAt | Microsoft Docs"
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
ms.assetid: 7979018f-1be3-4a13-9e8f-c84c7ed35288
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dd5ef17db177dfb1d532bfb88d1d0d77cdb7304
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="codepointat-method-string-javascript"></a>Método codePointAt (cadeia de caracteres) (JavaScript)
Retorna o ponto de código de um caractere Unicode UTF-16.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
stringObj.codePointAt(pos);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `stringObj`  
 Necessário. O objeto de cadeia de caracteres.  
  
 `pos`  
 Necessário. A posição do caractere.  
  
## <a name="remarks"></a>Comentários  
 Este método retorna valores de ponto de código, incluindo pontos de código astral (pontos de código com mais de quatro valores hexadecimais), para todos os caracteres UTF-16.  
  
 Se `pos` for menor que zero (0) ou maior que o tamanho da cadeia de caracteres, o valor retornado será `undefined`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o método `codePointAt`.  
  
```JavaScript  
var cp1 = "𠮷".codePointAt(0);  
var cp2 = 'abc'.codePointAt(1);  
  
if(console && console.log) {  
    console.log(cp1);  
    console.log(cp2);}  
  
// Output:  
// 0x20BB7  
// 98   
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
