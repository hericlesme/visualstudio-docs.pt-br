---
title: IDebugBoundBreakpoint2::SetPassCount | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBoundBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugBoundBreakpoint2::SetPassCount method
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 77a604f10029aa94dd1632aa656c3e7a2827e823
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugboundbreakpoint2setpasscount"></a>IDebugBoundBreakpoint2::SetPassCount
Define ou altera a contagem de passagem associada a este ponto de interrupção associado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```csharp  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `bpPassCount`  
 [in] O [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) estrutura que especifica a contagem de passagem.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro. Retorna `E_BP_DELETED` se o estado do objeto de ponto de interrupção associado é definido como `BPS_DELETED` (parte do [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) enumeração).  
  
## <a name="remarks"></a>Comentários  
 A contagem de passagem determina quando o ponto de interrupção é disparado. A fase atual ou a contagem de ocorrências pode ser obtida chamando o [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md) método.  
  
 Qualquer conta de passagem que foi previamente associada este ponto de interrupção será perdida.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)