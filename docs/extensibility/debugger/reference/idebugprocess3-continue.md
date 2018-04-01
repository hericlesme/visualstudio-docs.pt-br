---
title: IDebugProcess3::Continue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f666f35a71f65b839073e7d360bc357627fb7c5f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
Continua a execução desse processo de um estado parado. Qualquer estado de execução anterior (como uma etapa) é preservado, e executar novamente o processo é iniciado.  
  
> [!NOTE]
>  Esse método deve ser usado em vez de [continuar](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Continue(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Continue(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pThread`  
 [in] Um [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa o thread para continuar.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retornará o código de erro.  
  
## <a name="remarks"></a>Comentários  
 Este método é chamado neste processo, independentemente de quantos processos estão sendo depurados ou processo que gerou o evento de interrupção. A implementação deve manter o estado de execução anterior (como uma etapa) e continuar a execução como se ela nunca foi interrompido antes de concluir a execução anterior. Ou seja, se um thread nesse processo estava executando uma operação percorrer e foi interrompido porque outro processo interrompido e, em seguida, `Continue` foi chamado, o thread deve concluir a operação percorrer original.  
  
 **Aviso** não enviar um evento de parada ou um evento (síncrono) imediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ao tratar essa chamada; caso contrário, o depurador pode travar.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)