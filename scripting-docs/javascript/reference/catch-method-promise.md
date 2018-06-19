---
title: Método catch (promessa) | Microsoft Docs
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
ms.assetid: 55266f6a-db4d-4de8-857a-8bc7d35ed4b8
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 307e5b2a501b038542a602df4538523a3fc6eccd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633986"
---
# <a name="catch-method-promise"></a>Método catch (Promessa)
Permite que você especifique o trabalho a ser realizado mediante a rejeição de uma promessa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
promise.catch(onRejected)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `promise`  
 Necessário. O objeto de promessa.  
  
 `onRejected`  
 Necessário. A função de processamento do erro a ser executada quando uma promessa é rejeitada.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="example"></a>Exemplo  
 No exemplo de código a seguir, a primeira chamada para o tempo limite retorna após 5.000 ms. Nesse código, a promessa é rejeitada e a função de processamento do erro é executada.  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(reject, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    console.log("done!");  
}).catch(err => {  
    console.log("error!");  
})  
  
// Output (after five seconds):  
// error!  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]