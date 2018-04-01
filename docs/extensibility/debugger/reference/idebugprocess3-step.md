---
title: IDebugProcess3::Step | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 25f8816ab73ae5db402ded81ec26f108621cd405
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
Faz com que o processo para a etapa de uma instrução ou instrução.  
  
> [!NOTE]
>  Esse método deve ser usado em vez de [etapa](../../../extensibility/debugger/reference/idebugprogram2-step.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Step(  
   IDebugThread2* pThread,  
   STEPKIND       sk,  
   STEPUNIT       step,  
);  
```  
  
```csharp  
int Step(  
   IDebugThread2 pThread,   
   enum_STEPKIND sk,   
   enum_STEPUNIT step  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pThread`  
 [in] Um [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa o thread que está sendo passado.  
  
 `sk`  
 [in] Uma da [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) valores.  
  
 `step`  
 [in] Uma da [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) valores.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará o código de erro.  
  
## <a name="remarks"></a>Comentários  
 Caso haja qualquer sincronização de threads ou a comunicação entre threads, outros threads no processo devem ser executado quando um determinado thread está nivelado.  
  
 **Aviso** não enviar um evento de parada ou um evento (síncrono) imediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ao tratar essa chamada; caso contrário, o depurador pode travar.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)   
 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)