---
title: Método substring (String) (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- substring
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- substrings
- substring method
ms.assetid: 9cf9a005-cbe3-42fd-828b-57a39f54224c
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15ebaadc7b24fa97f531a22f6deb1453ff52b3e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640926"
---
# <a name="substring-method-string-javascript"></a>Método substring (String) (JavaScript)
Retorna a subcadeia de caracteres no local especificado em uma `String` objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
      strVariable. substring(start [, end])  
"String Literal".substring(start [, end])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `start`  
 Necessário. O inteiro do índice de base zero que indica o início da subcadeia de caracteres.  
  
 `end`  
 Opcional. O inteiro do índice de base zero que indicam o final da subcadeia de caracteres. A subcadeia de caracteres inclui os caracteres até, mas não incluindo, o caractere indicado pelo `end`.  
  
 Se `end` for omitido, os caracteres de `start` até o final da cadeia de caracteres original são retornados.  
  
## <a name="remarks"></a>Comentários  
 O `substring` método retorna uma cadeia de caracteres que contém a subcadeia de caracteres `start` até, mas não incluindo `end`.  
  
 O **subcadeia de caracteres** método usa o menor valor de `start` e `end` como o ponto de início da subcadeia de caracteres. Por exemplo, strvar.substring (0, 3 **)** e a mesma subcadeia de caracteres de retorno de strvar.substring (3, 0).  
  
 Se qualquer um dos `start` ou `end` é `NaN` ou negativo, ele é substituído por zero.  
  
 O comprimento da subcadeia de caracteres é igual ao valor absoluto da diferença entre `start` e `end`. Por exemplo, o comprimento da subcadeia de caracteres retornados em strvar.substring (0, 3) e strvar.substring (3, 0) é três.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do **subcadeia de caracteres** método.  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substring(10, 15);  
document.write(ss);  
  
// Output:  
// brown  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método substr (String)](../../javascript/reference/substr-method-string-javascript.md)