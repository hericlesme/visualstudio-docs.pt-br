---
title: IDebugInterceptExceptionCompleteEvent2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugInterceptExceptionCompleteEvent2
helpviewer_keywords: IDebugInterceptExceptionCompleteEvent2
ms.assetid: 8ebc256b-5428-4ed6-a505-6aedc8242b8e
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 588730d8e30044c5d5b00297a641beb9e45b17c4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebuginterceptexceptioncompleteevent2"></a>IDebugInterceptExceptionCompleteEvent2
Essa interface é enviada pelo mecanismo de depuração (DE) para o Gerenciador de sessão de depuração (SDM) quando o DE concluiu a manipulação de um evento interceptado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugInterceptExceptionCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O DE implementa essa interface para relatar que o processamento de uma exceção interceptada foi concluído. O [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface deve ser implementada no mesmo objeto dessa interface. Usa o SDM [QueryInterface](/cpp/atl/queryinterface) para acessar o `IDebugEvent2` interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O DE cria e envia esse objeto de evento para a conclusão de uma exceção interceptada de relatório. O evento é enviado usando o [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) função de retorno de chamada que é fornecida pelo SDM quando anexado ao programa que está sendo depurado.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 O `IDebugInterceptExceptionCompleteEvent2` interface implementa os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetInterceptCookie](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2-getinterceptcookie.md)|Retorna o valor exclusivo associado com a exceção tratada.|  
  
## <a name="remarks"></a>Comentários  
 Esse evento será enviado pela [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) quando esse método for concluída com êxito o tratamento de exceção interceptada.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)