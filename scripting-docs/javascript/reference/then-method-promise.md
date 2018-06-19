---
title: Método Then (Promise) | Microsoft Docs
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
ms.assetid: c7f3259d-78f7-4ca7-8bdf-99fbd3f41e8d
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeb97fae19ca9923280b5099e3e4d8c839fa2815
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640206"
---
# <a name="then-method-promise"></a>Método then (Promise)
Permite que você especifique o trabalho a ser realizado mediante o cumprimento de uma promessa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
promise.then(onCompleted, onRejected);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `promise`  
 Necessário. O objeto de promessa.  
  
 `onCompleted`  
 Necessário. A função de processamento de cumprimento a ser executada quando a promessa for concluída com êxito.  
  
 `onRejected`  
 Opcional. A função de processamento do erro a ser executada quando a promessa é rejeitada.  
  
## <a name="remarks"></a>Comentários  
 Uma promessa deve ser concluída com um valor ou rejeitada com um motivo. O método `then` do objeto Promise é executado quando a promessa é concluída ou rejeitada, o que ocorrer primeiro. Se a promessa for concluída com êxito, a função de processamento de cumprimento do método `then` é executada. Se a promessa for rejeitada, a função de processamento de erro do método `then` (ou o método `catch`) é executada.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como chamar uma função (`timeout`) que retorna uma promessa. O processador de cumprimento do método `then` é executado após o tempo limite de 5000 ms expirar.  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
// Note: This code uses arrow function syntax  
var m = timeout(5000).then(() => {  
    console.log("done!");  
})  
  
// Output (after 5 seconds):  
// done!  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Promise](../../javascript/reference/promise-object-javascript.md)