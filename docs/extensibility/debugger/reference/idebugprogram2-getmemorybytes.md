---
title: IDebugProgram2::GetMemoryBytes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetMemoryBytes
helpviewer_keywords:
- IDebugProgram2::GetMemoryBytes
ms.assetid: 1cdedb47-caf8-468e-aaf4-163f16afb403
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 289a1f7e2802fcf8187f74ec803af71cfb4a6bc0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogram2getmemorybytes"></a>IDebugProgram2::GetMemoryBytes
Recupera os bytes de memória ocupados pelo programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMemoryBytes(   
   IDebugMemoryBytes2** ppMemoryBytes  
);  
```  
  
```csharp  
int GetMemoryBytes(   
   out IDebugMemoryBytes2 ppMemoryBytes  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppMemoryBytes`  
 [out] Retorna um [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) objeto que representa os bytes de memória do programa.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Os bytes de memória, conforme representado pelo [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) objeto é para a imagem do programa na memória e não toda a memória que foi alocada quando o programa foi executado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)