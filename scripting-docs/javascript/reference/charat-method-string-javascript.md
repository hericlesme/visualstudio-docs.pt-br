---
title: "Método charAt (String) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: charAt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- String object, returning characters
- charAt method
- characters, returning part of
ms.assetid: 63173e15-17f6-47c5-8f94-98ef1eb04c1a
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 201d85fec4ba184f0842c7401d986650b9ee078c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="charat-method-string-javascript"></a>Método charAt (String) (JavaScript)
Retorna o caractere no índice especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
strObj. charAt(index)  
```  
  
## <a name="parameters"></a>Parâmetros  
 `strObj`  
 Necessário. Qualquer `String` literal de cadeia de caracteres ou objeto.  
  
 `index`  
 Necessário. O índice de base zero do caractere desejado.  
  
## <a name="remarks"></a>Comentários  
 O `charAt` método retorna um valor de caractere igual ao caractere no local especificado `index`. O primeiro caractere em uma cadeia de caracteres está no índice 0, o segundo é no índice 1 e assim por diante. Valores de `index` que estão fora do intervalo retornar uma cadeia de caracteres vazia.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do `charAt` método:  
  
```JavaScript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";  
document.write(str.charAt(str.length - 1));  
  
// Output: Z  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto de cadeia de caracteres](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Objeto String](../../javascript/reference/string-object-javascript.md)