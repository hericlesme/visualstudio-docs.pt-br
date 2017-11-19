---
title: "Função Debug mstraceasynccallbackstarting | Microsoft Docs"
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
ms.assetid: 0e2ca7c4-103c-44f2-b76c-102fb1e42543
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49203cdf16e7cbd74493c882d9cf17b7629da79a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="debugmstraceasynccallbackstarting-function"></a>Função Debug.msTraceAsyncCallbackStarting
Associa a pilha de retorno de chamada a uma operação assíncrona previamente especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.msTraceAsyncCallbackStarting(asyncOperationId)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `asyncOperationId`  
 Necessário. A identificação associada com a operação assíncrona.  
  
## <a name="remarks"></a>Comentários  
 Chame essa função na função de retorno de chamada para a operação assíncrona após a chamada para `Debug.msTraceAsyncOperationCompleted`.  
  
> [!NOTE]
>  Algumas ferramentas de depuração não exibem as informações enviadas para o depurador.  
  
 O `asyncOperationId` deve corresponder ao nome da operação retornado anteriormente de `Debug.msTraceAsyncOperationStarting`.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra um exemplo de rastreamento de uma chamada assíncrona de um aplicativo [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
```JavaScript  
function asyncWrapperFunction() {  
    var opID = Debug.msTraceAsyncOperationStarting('async trace');  
    doSomethingAsync().then(function (result) {  
        Debug.msTraceAsyncOperationCompleted(opID, Debug.MS_ASYNC_OP_STATUS_SUCCESS);  
        Debug.msTraceAsyncCallbackStarting(opID);  
        // Process result of async operation.  
    }, function (error) {  
        Debug.msTraceAsyncOperationCompleted(opID, Debug.MS_ASYNC_OP_STATUS_ERROR);  
        Debug.msTraceAsyncCallbackStarting(opID);  
    });  
  
    Debug.msTraceAsyncCallbackCompleted();  
}  
  
function doSomethingAsync() {  
    return WinJS.Promise.as(true);  
}  
  
asyncWrapperFunction();  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]