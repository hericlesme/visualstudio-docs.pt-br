---
title: Método join (Array) (JavaScript) | Microsoft Docs
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
- join
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Join method
- concatenating strings, join method
- arrays [Visual Studio], joining
ms.assetid: 20f8fde1-014b-488e-9008-464a86e6b21f
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4591b12b3556384fef3e367d20cf9545d2f3dedd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637606"
---
# <a name="join-method-array-javascript"></a>Método join (Array) (JavaScript)
Adiciona todos os elementos de uma matriz separada pela cadeia de caracteres do separador especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
arrayObj.join([separator])   
```  
  
## <a name="parameters"></a>Parâmetros  
 `arrayObj`  
 Necessário. Um objeto `Array`.  
  
 `separator`  
 Opcional. Uma cadeia de caracteres usada para separar um elemento de uma matriz do próximo no resultante `String`. Se omitido, os elementos da matriz são separados por vírgula.  
  
## <a name="remarks"></a>Comentários  
 Se qualquer elemento da matriz é **indefinido** ou `null`, ela será tratada como uma cadeia de caracteres vazia.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do **junção** método.  
  
```JavaScript  
var a, b;  
a = new Array(0,1,2,3,4);  
b = a.join("-");  
document.write(b);  
  
// Output:  
// 0-1-2-3-4  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Objeto String](../../javascript/reference/string-object-javascript.md)