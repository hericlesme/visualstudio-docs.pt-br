---
title: "Função JsSetProjectionEnqueueCallback | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c751ccef-20d2-4d41-9568-1c54adf47cdf
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8abdc575c5066ade4a700a0c88e09e3476a65366
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2017
---
# <a name="jssetprojectionenqueuecallback-function"></a>Função JsSetProjectionEnqueueCallback
Define o retorno de chamada a ser usado para invocar uma conclusão de projeção de volta para o thread requerido pelo chamador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
STDAPI_(JsErrorCode) JsSetProjectionEnqueueCallback(  
   _In_ JsProjectionEnqueueCallback projectionEnqueueCallback,  
   _In_opt_ void *projectionEnqueueContext);  
  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `projectionEnqueueContext`  
 O retorno de chamada que será invocado sempre que uma conclusão de projeção ocorrer em um thread em segundo plano.  
  
 `callbackState`  
 O contexto do aplicativo fornecido para `projectionEnqueueContext`.  
  
## <a name="return-value"></a>Valor de retorno  
 O código `JsNoError` se a operação foi bem-sucedida, caso contrário, um código de falha.  
  
## <a name="remarks"></a>Comentários  
 Exige um contexto de script ativo.  
  
 A chamada deve estar vindo de um apartment COM diferente ou de um thread diferente no mesmo MTA.  
  
 Essa API tem suporte apenas no modo de Borda.  
  
> [!CAUTION]
>  PInvoke não tem suporte atualmente para esta API.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** jsrt.h  
  
## <a name="see-also"></a>Consulte também  
 [Referência (Tempo de Execução do JavaScript)](../chakra-hosting/reference-javascript-runtime.md)