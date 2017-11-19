---
title: IDebugBoundBreakpoint2::SetCondition | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBoundBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugBoundBreakpoint2::SetCondition method
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5d5d6f04e420ed7268c009467f74c020d429ab2b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugboundbreakpoint2setcondition"></a>IDebugBoundBreakpoint2::SetCondition
Define ou altera a condição associada a este ponto de interrupção associado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```csharp  
int SetCondition(   
   enum_BP_CONDITION bpCondition  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `bpCondition`  
 [in] Um valor da [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) enumeração que descreve a condição.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro. Retorna `E_BP_DELETED` se o estado do objeto de ponto de interrupção associado é definido como `BPS_DELETED` (parte do [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) enumeração).  
  
## <a name="remarks"></a>Comentários  
 Qualquer condição que foi previamente associada este ponto de interrupção é perdida.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)