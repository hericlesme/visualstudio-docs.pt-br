---
title: "Método Shift (Array) (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: shift
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: shift method
ms.assetid: f33baec5-f67e-4760-b7c1-553727bd0423
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 664c3f764950b329cea8356f5b350ee917f0a60f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="shift-method-array-javascript"></a>Método shift (Array) (JavaScript)
Remove o primeiro elemento de uma matriz e o retorna.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
arrayObj.shift( )  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Obrigatório `arrayObj` referência é um `Array` objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna o elemento removido da matriz.  
  
## <a name="remarks"></a>Comentários  
 O exemplo a seguir ilustra o uso do método `shift`.  
  
```JavaScript  
var arr = new Array(10, 11, 12);  
while (arr.length > 0)  
    {  
    var i = arr.shift();  
    document.write (i.toString() + " ");  
    }  
  
// Output:   
// 10 11 12  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método unshift (Array)](../../javascript/reference/unshift-method-array-javascript.md)