---
title: IDebugProgram2::Step | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 10685adb27c9bf2e962beccb7e68f19ce5c27eeb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31118551"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Executa uma etapa.  
  
> [!NOTE]
>  Este método é preterido. Use o [etapa](../../../extensibility/debugger/reference/idebugprocess3-step.md) método em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```csharp  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pThread`  
 [in] Um [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa o thread que está sendo passado.  
  
 `sk`  
 [in] Um valor da [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) enumeração que especifica o tipo de etapa.  
  
 `step`  
 [in] Um valor da [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) enumeração que especifica a unidade de etapa (por exemplo, pela instrução ou instrução).  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Caso haja qualquer sincronização de threads ou a comunicação entre threads, outros threads no programa devem ser executado quando um determinado thread está nivelado.  
  
> [!WARNING]
>  Não enviar um evento de parada ou um evento (síncrono) imediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ao tratar essa chamada; caso contrário, o depurador pode travar.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)