---
title: IDebugBoundBreakpoint2::GetHitCount | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBoundBreakpoint2::GetHitCount
helpviewer_keywords:
- GetHitCount method
- IDebugBoundBreakpoint2::GetHitCount method
ms.assetid: 23481f37-047c-41d2-8286-4da1f4084961
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a955c56eb8b3705dd967e2c070ce140abe930043
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugboundbreakpoint2gethitcount"></a>IDebugBoundBreakpoint2::GetHitCount
Obtém a contagem de ocorrências atual para este ponto de interrupção associado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetHitCount(   
   DWORD* pdwHitCount  
);  
```  
  
```csharp  
int GetHitCount(   
   out uint pdwHitCount  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwHitCount`  
 [out] Retorna a contagem de ocorrências.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro. Retorna `E_BP_DELETED` se o estado do objeto de ponto de interrupção associado é definido como `BPS_DELETED` (parte do [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) enumeração).  
  
## <a name="remarks"></a>Comentários  
 A contagem de ocorrências é o número de vezes que este ponto de interrupção foi disparado durante a execução da sessão atual.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)