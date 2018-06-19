---
title: Método toString (Array) | Microsoft Docs
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
ms.assetid: 71fbea85-3e00-41b0-b167-25e4281e5e8a
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6dc7cbf843e47ffc2d21f5a2b1d03c43e675a130
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640406"
---
# <a name="tostring-method-array"></a>Método toString (Array)
Retorna uma representação em cadeia de caracteres de uma matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
array.toString()  
```  
  
## <a name="parameters"></a>Parâmetros  
 `array`  
 Necessário. A matriz para representar como uma cadeia de caracteres.  
  
## <a name="return-value"></a>Valor de retorno  
 A representação de cadeia de caracteres da matriz.  
  
## <a name="remarks"></a>Comentários  
 Os elementos de um `Array` são convertidos em cadeias de caracteres. As cadeias de caracteres resultantes são concatenadas e separadas por vírgulas.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do **toString** método com uma matriz.  
  
```JavaScript  
var arr = [1, 2, 3, 4];  
var s = arr.toString();  
document.write(s);  
  
// Output: 1,2,3,4  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]