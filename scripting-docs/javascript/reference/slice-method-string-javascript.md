---
title: "Método (String) (JavaScript) Slice | Microsoft Docs"
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
- slice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strings [Visual Studio], returning characters
- slice method
ms.assetid: 80cd77a6-3718-492e-8e96-f909d8721d91
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1baa0a05a2d6aa8c06cc962761c8e557632d034c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="slice-method-string-javascript"></a>Método slice (Cadeia de Caracteres) (JavaScript)
Retorna uma seção de uma cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
stringObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `stringObj`  
 Necessário. Um objeto `String` ou literal de cadeia de caracteres.  
  
 `start`  
 Necessário. O índice para o início da parte especificada de `stringObj`.  
  
 `end`  
 Opcional. O índice até o final da parte especificada de `stringObj`. A subcadeia de caracteres inclui os caracteres até, mas não incluindo, o caractere indicado pelo `end`. Se esse valor não for especificado, a subcadeia de caracteres continua até o final de `stringObj`.  
  
## <a name="remarks"></a>Comentários  
 O `slice` método retorna um `String` objeto que contém a parte especificada de `stringObj`.  
  
 O `slice` método copia até, mas não incluindo, o caractere indicado pelo `end`.  
  
 Se `start` é negativo, ele será tratado como *comprimento*  +  `start` onde *comprimento* é o comprimento da cadeia de caracteres. Se `end` é negativo, ele será tratado como *comprimento* + `end`. Se `end` é omitido, copiando continua até o final de `stringObj`. Se `end` ocorre antes de `start`, sem caracteres são copiados para a nova cadeia de caracteres.  
  
## <a name="example"></a>Exemplo  
 No primeiro exemplo, o `slice` método retorna a cadeia de caracteres inteira. No segundo exemplo, o `slice` método retorna a cadeia de caracteres inteira, exceto o último caractere.  
  
```JavaScript  
var str1 = "all good boys do fine";  
  
var slice1 = str1.slice(0);  
var slice2 = str1.slice(0,-1);  
var slice3 = str1.slice(4);  
var slice4 = str1.slice(4, 8);  
  
document.write(slice1 + "<br/>");  
document.write(slice2 + "<br/>");  
document.write(slice3 + "<br/>");  
document.write(slice4);  
  
// Output:  
// all good boys do fine  
// all good boys do fin  
// good boys do fine  
// good  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Aplica-se a**: [objeto de cadeia de caracteres](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Consulte também  
 [Método slice (Array)](../../javascript/reference/slice-method-array-javascript.md)