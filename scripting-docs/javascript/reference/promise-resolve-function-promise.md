---
title: Função Promise resolve (Promise) | Microsoft Docs
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
ms.assetid: 0fb6bff9-54ab-41be-97d7-04f7e6fe9cff
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d815c9c23da48c877f7f1d995df8991429375e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638556"
---
# <a name="promiseresolve-function-promise"></a>Função promise.resolve (Promise)
Cria uma nova promessa resolvida com resultado igual ao seu argumento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Promise.resolve(x)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `x`  
 Necessário. O valor retornado com a promessa concluída.  
  
## <a name="remarks"></a>Comentários  
 A função de processamento de cumprimento do método `then` é executada quando o objeto de promessa concluído é retornado.  
  
## <a name="example"></a>Exemplo  
  
```JavaScript  
var p = Promise.resolve('success');  
p.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Promise](../../javascript/reference/promise-object-javascript.md)