---
title: IDebugProgram2::Continue | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::Continue
helpviewer_keywords: IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 81a8bf23ee0272f448c49b6d58d194d3ba261509
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Continua executando esse programa de um estado parado. Qualquer estado de execução anterior (como uma etapa) é preservado, e o programa inicia a execução novamente.  
  
> [!NOTE]
>  Este método é preterido. Use o [continuar](../../../extensibility/debugger/reference/idebugprocess3-continue.md) método em vez disso.  
  
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
 [in] Um [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa o thread.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Este método é chamado neste programa, independentemente de quantos aplicativos estão sendo depurados, ou o programa que gerou o evento de interrupção. A implementação deve manter o estado de execução anterior (como uma etapa) e continuar a execução como se ela nunca foi interrompido antes de concluir a execução anterior. Ou seja, se um thread em que o programa estava executando uma operação percorrer e foi interrompido porque outro programa interrompido e, em seguida, esse método foi chamado, o programa deve concluir a operação percorrer original.  
  
> [!WARNING]
>  Não enviar um evento de parada ou um evento (síncrono) imediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ao tratar essa chamada; caso contrário, o depurador pode travar.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)