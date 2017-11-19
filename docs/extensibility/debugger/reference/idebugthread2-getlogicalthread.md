---
title: IDebugThread2::GetLogicalThread | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2::GetLogicalThread
helpviewer_keywords: IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a0f2eaba3176ed5d77a2857a4325a06b16417380
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Mecanismos de depuração não implementam este método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetLogicalThread(   
   IDebugStackFrame2*     pStackFrame,  
   IDebugLogicalThread2** ppLogicalThread  
);  
```  
  
```csharp  
int GetLogicalThread(   
   IDebugStackFrame2        pStackFrame,  
   out IDebugLogicalThread2 ppLogicalThread  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pStackFrame`  
 [in] Um [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) objeto que representa o quadro de pilhas.  
  
 `ppLogicalThread`  
 [out] Retorna um `IDebugLogicalThread2` interface que representa o thread lógico associado. Uma implementação do mecanismo de depuração deve defini-lo como um valor nulo.  
  
## <a name="return-value"></a>Valor de retorno  
 Depurar implementações de mecanismo sempre retornam `E_NOTIMPL`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)