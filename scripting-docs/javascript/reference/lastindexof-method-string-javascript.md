---
title: "Método lastIndexOf (String) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: lastIndexOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lastIndexOf method, string
- string, lastIndexOf method
ms.assetid: 1ed36ccd-0f0b-4f16-be45-0567207670af
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0fa0f35e970435a4d0296493c20afdeaac128cae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="lastindexof-method-string-javascript"></a>Método lastIndexOf (String) (JavaScript)
Retorna a última ocorrência de uma subcadeia de caracteres na cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
strObj.lastIndexOf(substring[, startindex])  
```  
  
## <a name="parameters"></a>Parâmetros  
 `strObj`  
 Necessário. Um objeto `String` ou literal de cadeia de caracteres.  
  
 `substring`  
 Necessário. A subcadeia de caracteres a ser pesquisado.  
  
 `startindex`  
 Opcional. O índice no qual iniciar a pesquisa. Se omitido, a pesquisa começará no final da cadeia de caracteres.  
  
## <a name="remarks"></a>Comentários  
 O **lastIndexOf** método retorna um valor inteiro que indica o início da subcadeia de caracteres dentro de `String` objeto. Se a subcadeia de caracteres não for encontrada, -1 será retornado.  
  
 Se `startindex` for negativo, `startindex` será tratado como zero. Se for maior do que o maior índice de posição de caractere, ele será tratado como o maior índice possíveis.  
  
 Pesquisa é executada a partir do último caractere na cadeia de caracteres. Caso contrário, esse método é idêntico ao **indexOf**.  
  
 O exemplo a seguir ilustra o uso do **lastIndexOf** método.  
  
```JavaScript  
var str = "time, time";  
  
var s = "";  
s += "time is at position " + str.lastIndexOf("time");  
s += "<br />";  
s += "abc is at position " + str.lastIndexOf("abc");  
  
document.write(s);  
  
// Output:  
// time is at position 6  
// abc is at position -1  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Aplica-se a**: [objeto de cadeia de caracteres](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método indexOf (String)](../../javascript/reference/indexof-method-string-javascript.md)