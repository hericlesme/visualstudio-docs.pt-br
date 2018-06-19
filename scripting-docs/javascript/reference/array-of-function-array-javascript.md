---
title: Função Array of (Array) (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2884dda3-65d1-4990-9afe-87865c2d4f7f
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 042315bbc3b956e92fff866f7d403b6f87726a74
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633976"
---
# <a name="arrayof-function-array-javascript"></a>Função array.of (Array) (JavaScript)
Retorna uma matriz dos argumentos passados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Array.of(element0[, element1][, ...][,elementN]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `element0,...,elementN`  
 Opcional. Os elementos a serem colocados na matriz. Isso cria uma matriz com n+1 elementos e um comprimento de n+1.  
  
## <a name="remarks"></a>Comentários  
 Essa função é semelhante a chamar `new Array(args)`, mas `Array.of` não inclui um comportamento especial quando um argumento é passado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma matriz de números passados.  
  
```JavaScript  
var arr = Array.of(1, 2, 3);  
// arr[0] == 1   
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra a diferença entre usar `Array.of` e `new Array`.  
  
```JavaScript  
var arr1 = Array.of(3);  
// arr1[0] == 3  
  
// With new Array, a single argument specifies  
// the length of the new array.  
var arr2 = new Array(3);  
// arr2[0] is undefined  
// arr2.length == 3  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]