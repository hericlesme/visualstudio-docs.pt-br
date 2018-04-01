---
title: IDebugPendingBreakpoint2::SetPassCount | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ab9a8ceec8c0f3a1b8d6c3c18fcf9c5c2a5b0b91
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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