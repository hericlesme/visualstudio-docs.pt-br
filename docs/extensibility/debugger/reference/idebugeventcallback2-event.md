---
title: IDebugEventCallback2::Event | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8ea52b8be040df50da1585165599c4fdea635557
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31117651"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Envia notificação de eventos de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Event(   
   IDebugEngine2*  pEngine,  
   IDebugProcess2* pProcess,  
   IDebugProgram2* pProgram,  
   IDebugThread2*  pThread,  
   IDebugEvent2*   pEvent,  
   REFIID          riidEvent,  
   DWORD           dwAttrib  
);  
```  
  
```csharp  
int Event(   
   IDebugEngine2  pEngine,  
   IDebugProcess2 pProcess,  
   IDebugProgram2 pProgram,  
   IDebugThread2  pThread,  
   IDebugEvent2   pEvent,  
   ref Guid       riidEvent,  
   uint           dwAttrib  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pEngine`  
 [in] Um [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) objeto que representa o mecanismo de depuração (DE) que está enviando esse evento. A DE é necessária para preencher este parâmetro.  
  
 `pProcess`  
 [in] Um [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objeto que representa o processo no qual o evento ocorre. Esse parâmetro é preenchido, o Gerenciador de sessão de depuração (SDM). A DE sempre passa um valor nulo para esse parâmetro.  
  
 `pProgram`  
 [in] Um [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa o programa no qual esse evento ocorre. Para a maioria dos eventos, esse parâmetro não é um valor nulo.  
  
 `pThread`  
 [in] Um [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa o thread em que este evento ocorre. Para interromper eventos, esse parâmetro não pode ser um valor nulo como o quadro de pilhas é obtido a partir desse parâmetro.  
  
 `pEvent`  
 [in] Um [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) objeto que representa o evento de depuração.  
  
 `riidEvent`  
 [in] GUID que identifica qual interface de eventos para obter a partir de `pEvent` parâmetro.  
  
 `dwAttrib`  
 [in] Uma combinação de sinalizadores do [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) enumeração.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Ao chamar esse método, o `dwAttrib` parâmetro deve corresponder ao valor retornado do [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) método como chamado no objeto de evento passado a `pEvent` parâmetro.  
  
 Todos os eventos de depuração são lançados assincronamente, independentemente se um evento em si é assíncrono ou não. Quando a DE chama esse método, o valor de retorno não indica se o evento foi processado, apenas se o evento foi recebido. Na verdade, na maioria das circunstâncias, o evento não foi processado quando este método retorna.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)