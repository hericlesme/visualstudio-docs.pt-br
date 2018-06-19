---
title: Constantes de depuração | Microsoft Docs
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
ms.assetid: 76b572ee-bad0-404e-9fd4-841c9af35642
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2c50181dc9f40d8665d6caca407232231682d63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636146"
---
# <a name="debug-constants"></a>Constantes de depuração
Depurar constantes retorno valores constantes que são propriedades do `Debug` objeto.  
  
## <a name="debug-object-constants"></a>Constantes do objeto de depuração  
 A tabela a seguir lista os valores constantes que são propriedades do [objeto Debug](../../javascript/reference/debug-object-javascript.md).  
  
|Constante|Descrição|Valor|  
|--------------|-----------------|-----------|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ASSIGN_DELEGATE`|O item de trabalho síncrono atribuído um retorno de chamada ou uma continuação para ser executado por uma operação assíncrona.|0|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_JOIN`|O item de trabalho síncrono satisfeita parte de uma operação assíncrona de junção.|1|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CHOOSEANY`|O item de trabalho síncrono satisfeita uma operação assíncrona de escolha.|2|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_CANCEL`|O item de trabalho síncrono foi cancelado.|3|  
|`Debug.MS_ASYNC_CALLBACK_STATUS_ERROR`|O item de trabalho síncrono causou um erro em uma operação assíncrona.|4|  
|`Debug.MS_ASYNC_OP_STATUS_SUCCESS`|A operação assíncrona foi bem-sucedida.|1|  
|`Debug.MS_ASYNC_OP_STATUS_CANCELED`|A operação assíncrona foi cancelada.|2|  
|`Debug.MS_ASYNC_OP_STATUS_ERROR`|A operação assíncrona resultou em erro.|3|  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Função Debug. mstraceasyncoperationcompleted](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md)   
 [Função Debug.msUpdateAsyncCallbackRelation](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md)