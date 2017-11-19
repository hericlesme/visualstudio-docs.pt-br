---
title: comprimento da propriedade (String) (JavaScript) | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strings [Visual Studio], length
- Length property
- length property (String)
ms.assetid: 7dbd4a0e-c24e-4561-9b5b-e75e649a10a4
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 706a7f6986086f95613e09b9a8355eb5bc2702a7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-string-javascript"></a>Propriedade length (Cadeia de Caracteres) (JavaScript)
Retorna o comprimento de um objeto `String`.  
  
> [!WARNING]
>  Cadeias de caracteres do JavaScript são imutáveis, então o comprimento de uma cadeia de caracteres não pode ser modificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
      strVariable.length  
"String Literal".length   
```  
  
## <a name="remarks"></a>Comentários  
 O `length` propriedade contém um número inteiro que indica o número de caracteres a `String` objeto. O último caractere do `String` objeto tem um índice,`length` - 1.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como usar `length`. Cadeias de caracteres do JavaScript são imutáveis e não podem ser modificadas em vigor. No entanto, você pode gravar a cadeia de caracteres revertida em uma matriz e, em seguida, chamar `join` com o caractere vazio, o que produz uma cadeia de caracteres sem caracteres do separador.  
  
```JavaScript  
var str = "every good boy does fine";  
        var start = 0;  
        var end = str.length - 1;  
        var tmp = "";  
        var arr = new Array(end);  
  
        while (end >= 0) {  
            arr[start++] = str.charAt(end--);  
        }  
  
// Join the elements of the array with a   
        var str2 = arr.join('');  
        document.write(str2);  
  
// Output: enif seod yob doog yreve  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]