---
title: IDebugPendingBreakpoint2::SetPassCount | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 21e39c54249add3b5d57cd6db907256122aab56b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
Define ou altera a contagem de passagem associada com o ponto de interrupção pendente.  
  
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
 [in] Um [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) estrutura que contém a contagem de passagem.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro. Retorna `E_BP_DELETED` se o ponto de interrupção foi excluído.  
  
## <a name="remarks"></a>Comentários  
 Qualquer conta de passagem que foi previamente associada com o ponto de interrupção pendente será perdida. Todos os pontos de interrupção associados deste pendente de ponto de interrupção são chamados para definir sua contagem de passagem para o `bpPassCount` parâmetro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)