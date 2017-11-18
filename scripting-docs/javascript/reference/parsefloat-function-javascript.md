---
title: "Função parseFloat (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: parseFloat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: parseFloat method
ms.assetid: a7d87a69-1919-4623-be85-972e6376dd2d
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb8f6d179abba887542e59d083141534732ed42a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="parsefloat-function-javascript"></a>Função parseFloat (JavaScript)
Converte uma cadeia de caracteres em um número de ponto flutuante.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
parseFloat(numString)   
```  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `numString` argumento é uma cadeia de caracteres que contém um número de ponto flutuante.  
  
 O `parseFloat` função retorna um valor numérico igual ao número contido na `numString`. Se nenhum prefixo de `numString` pode ser analisado com êxito em um número de ponto flutuante, `NaN` (não um número) será retornado.  
  
```JavaScript  
parseFloat("abc")      // Returns NaN.  
parseFloat("1.2abc")   // Returns 1.2.  
```  
  
 Você pode testar `NaN` usando o `isNaN` função.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto Global](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Função isNaN](../../javascript/reference/isnan-function-javascript.md)   
 [Função parseInt](../../javascript/reference/parseint-function-javascript.md)   
 [Objeto String](../../javascript/reference/string-object-javascript.md)