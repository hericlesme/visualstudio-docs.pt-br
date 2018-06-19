---
title: Função Debug msupdateasynccallbackrelation | Microsoft Docs
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
ms.assetid: ee6a1efc-375c-4ce8-a4e8-8896ee29f849
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c47ed7f6313646dddf86dd766d7f1027b2d38ad
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636216"
---
# <a name="debugmsupdateasynccallbackrelation-function"></a>Função Debug.msUpdateAsyncCallbackRelation
Atualiza o status de relação entre um item de trabalho síncrono e a operação assíncrona associada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Debug.msUpdateAsyncCallbackRelation(relatedAsyncOperationId, relationType)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `relatedAsyncOperationId`  
 Necessário. A identificação associada com a operação assíncrona.  
  
 `relationType`  
 Opcional. O valor que especifica o status da relação.  
  
## <a name="remarks"></a>Comentários  
 O item de trabalho síncrono é normalmente a função de retorno de chamada da operação assíncrona. Essa função pode ser chamada quando você anular uma operação assíncrona, usar uma operação de união, ou em outros cenários.  
  
 Os valores possíveis para `relationType` incluem:  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`  
  
-   `Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`  
  
 Para obter mais informações, consulte [depurar constantes](../../javascript/reference/debug-constants.md).  
  
> [!NOTE]
>  Algumas ferramentas de depuração não exibem as informações enviadas para o depurador por essa função.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]