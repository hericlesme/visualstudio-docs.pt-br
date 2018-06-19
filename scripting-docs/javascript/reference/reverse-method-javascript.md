---
title: Método reverse (JavaScript) | Microsoft Docs
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
- reverse
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [Visual Studio], reversing elements
- reverse method
- transposing elements
ms.assetid: 02ab051b-79b8-4646-b502-381671e78c12
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a34385ccf89557688698b50384b3dfe359478df
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639706"
---
# <a name="reverse-method-javascript"></a>Método reverse (JavaScript)
Reverte os elementos em um `Array`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
arrayObj.reverse()   
```  
  
## <a name="parameters"></a>Parâmetros  
 `arrayObj`  
 Necessário. Qualquer objeto `Array`.  
  
## <a name="return-value"></a>Valor de retorno  
 A matriz invertida.  
  
## <a name="remarks"></a>Comentários  
 Obrigatório `arrayObj` referência é um `Array` objeto.  
  
 O `reverse` método inverte os elementos de uma `Array` objeto no local. Não cria um novo `Array` objeto durante a execução.  
  
 Se a matriz não é contígua, o `reverse` método cria elementos na matriz que preencher as lacunas na matriz. Cada um desses elementos criados tem o valor `undefined`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o uso do método `reverse`.  
  
```JavaScript  
var arr = new Array(0,1,2,3,4);   
var reverseArr = arr.reverse();  
document.write(reverseArr);  
  
// Output:  
// 4,3,2,1,0  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método concat (Array)](../../javascript/reference/concat-method-array-javascript.md)