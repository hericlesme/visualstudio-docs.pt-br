---
title: "Função String. fromcodepoint (JavaScript) | Microsoft Docs"
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
ms.assetid: 7c4c057b-c67a-4b10-afdd-4f75c7c5988c
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0905b392606bec9fb59b08a04129ce30cb013db1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="stringfromcodepoint-function-javascript"></a>Função String.fromCodePoint (JavaScript)
Retorna a cadeia de caracteres associada a um ponto de código Unicode UTF-16.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
String.fromCodePoint(...codePoints);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `...codePoints`  
 Necessário. Um parâmetro REST que especifica um ou mais valores de ponto de código UTF-16.  
  
## <a name="remarks"></a>Comentários  
 Essa função gera uma exceção `RangeError` se `...codePoints` não for um ponto de código UTF-16 válido.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar a função `fromCodePoint`.  
  
```JavaScript  
var str1 = String.fromCodePoint(0x20BB7);  
var str2 = String.fromCodePoint(98);  
var str3 = String.fromCodePoint(97, 98, 99);  
  
if(console && console.log) {  
    console.log(str1);  
    console.log(str2);  
    console.log(str3);  
}  
  
// Output:  
// 𠮷  
// b  
// abc   
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]