---
title: IDebugPortEvents2::Event | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c9f1394e09cc6b7b695d1d19dee1f46df09f8514
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
Esse método envia os eventos que significam a criação e destruição de processos e programas em uma porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Event(  
   IDebugCoreServer2* pServer,  
   IDebugPort2*       pPort,  
   IDebugProcess2*    pProcess,  
   IDebugProgram2*    pProgram,  
   IDebugEvent2*      pEvent,  
   REFIID             riidEvent  
);  
```  
  
```csharp  
int Event(  
   IDebugCoreServer2 pServer,   
   IDebugPort2       pPort,   
   IDebugProcess2    pProcess,   
   IDebugProgram2    pProgram,   
   IDebugEvent2      pEvent,   
   ref Guid          riidEvent  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pMachine`  
 [in] Um [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) objeto que representa o servidor de depuração (há um para cada instância de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]) no qual o evento ocorreu.  
  
 `pPort`  
 [in] Um [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) objeto que representa a porta na qual o evento ocorreu.  
  
 `pProcess`  
 [in] Um [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) objeto que representa o processo no qual o evento ocorreu.  
  
 `pProgram`  
 [in] Um [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa o programa no qual o evento ocorreu.  
  
 `pEvent`  
 [in] Um [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) objeto que identifica o evento. Os eventos possíveis são os seguintes:  
  
-   [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)  
  
-   [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)  
  
-   [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
-   [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)  
  
 `riidEvent`  
 [in] O GUID do evento. Como o evento é convertido em [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) antes de chamar esse método, esse identificador torna mais fácil determinar quais eventos estão sendo enviados.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)