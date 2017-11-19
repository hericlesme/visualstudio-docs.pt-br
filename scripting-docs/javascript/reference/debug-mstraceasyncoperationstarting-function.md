---
title: "Função Debug mstraceasyncoperationstarting | Microsoft Docs"
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
ms.assetid: c8458264-07e0-4cd6-8528-ff7cf009cf9e
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a50c58e352d40a06192664cdf7424348be02d466
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="debugmstraceasyncoperationstarting-function"></a>Função Debug.msTraceAsyncOperationStarting
Inicia um rastreamento de uma operação assíncrona.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.msTraceAsyncOperationStarting(operationName)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `operationName`  
 Necessário. Uma cadeia de caracteres que identifica uma operação assíncrona. Se `operationName` for nulo ou indefinido, uma cadeia de caracteres vazia é usada para o nome da operação.  
  
## <a name="return-value"></a>Valor de retorno  
 Um valor inteiro que representa a ID da operação.  
  
## <a name="remarks"></a>Comentários  
 Chame esse método antes de iniciar a operação assíncrona.  
  
> [!NOTE]
>  Algumas ferramentas de depuração não exibem as informações enviadas para o depurador.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra um exemplo de instrumentação de uma chamada assíncrona de um aplicativo [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
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