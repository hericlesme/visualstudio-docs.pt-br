---
title: IDebugThread2::Suspend | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f865194e023ed0311f06988dd026fb2b123aaf4a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Suspende um thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Suspend (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
HRESULT Suspend (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwSuspendCount`  
 [out] Retorna a contagem de suspensão após a operação de suspensão.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Cada chamada para esse método incrementa a contagem de suspensão acima de 0. Essa contagem suspend é exibida no **Threads** janela de depuração.  
  
 Para cada chamada para esse método, deve haver uma chamada posterior para o [retomar](../../../extensibility/debugger/reference/idebugthread2-resume.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)