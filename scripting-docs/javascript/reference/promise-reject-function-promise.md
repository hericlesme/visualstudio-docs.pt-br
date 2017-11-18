---
title: "Função Promise Reject (promessa) | Microsoft Docs"
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
ms.assetid: 9746e15b-9717-4e36-bf6b-910dcc6cd667
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0711bdd8a478d4ea07ee40ea6822af3c8c4ac610
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="promisereject-function-promise"></a>Função Promise.reject (Promessa)
Cria uma nova promessa rejeitada com resultado igual ao argumento passado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Promise.reject(r);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `r`  
 Necessário. O motivo pelo qual a promessa foi rejeitada.  
  
## <a name="remarks"></a>Comentários  
 A função de tratamento de erro do método `then` ou `catch` é executada quando a promessa rejeitada é retornada.  
  
## <a name="example"></a>Exemplo  
  
```JavaScript  
var p = Promise.reject('failure');  
p.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Promise](../../javascript/reference/promise-object-javascript.md)