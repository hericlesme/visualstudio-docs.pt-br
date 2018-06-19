---
title: Função Debug mstraceasyncoperationcompleted | Microsoft Docs
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
ms.assetid: 9b628b71-61f1-478a-857f-5e1f607db56c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41370257042a2de50d21eba51c299198a6bfb72a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636226"
---
# <a name="debugmstraceasyncoperationcompleted-function"></a>Função Debug.msTraceAsyncOperationCompleted
Indica que uma operação assíncrona foi concluída.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.msTraceAsyncOperationCompleted(asyncOperationId, status)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `asyncOperationId`  
 Necessário. A identificação associada com uma operação assíncrona.  
  
 `status`  
 Opcional. O status da operação assíncrona. Se não for especificado, é usado `Debug.MS_ASYNC_OP_STATUS_SUCCESS`.  
  
## <a name="remarks"></a>Comentários  
 Chame essa função quando a operação assíncrona for concluída.  
  
 O `asyncOperationId` deve corresponder à identificação da operação retornada anteriormente de `Debug.msTraceAsyncOperationStarting`.  
  
 Os valores possíveis para `status` incluem:  
  
-   `Debug.MS_ASYNC_OP_STATUS_SUCCESS`  
  
-   `Debug.MS_ASYNC_OP_STATUS_CANCELED`  
  
-   `Debug.MS_ASYNC_OP_STATUS_ERROR`  
  
> [!NOTE]
>  Algumas ferramentas de depuração não exibem as informações enviadas para o depurador.  
  
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