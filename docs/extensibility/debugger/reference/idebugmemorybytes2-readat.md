---
title: IDebugMemoryBytes2::ReadAt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 612a065286723e3c2b68a9ce5bd31c850d030959
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Lê uma sequência de bytes, começando em um local específico.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT ReadAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory,  
   DWORD*                pdwRead,  
   DWORD*                pdwUnreadable  
);  
```  
  
```csharp  
int ReadAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory,  
   out uint             pdwRead,  
   ref uint             pdwUnreadable  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pStartContext`  
 [in] O [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objeto que especifica onde começar a ler bytes.  
  
 `dwCount`  
 [in] O número de bytes a serem lidos. Também especifica o comprimento do `rgbMemory` matriz.  
  
 `rgbMemory`  
 [out no] Matriz preenchido com os bytes realmente lidos.  
  
 `pdwRead`  
 [out] Retorna o número de bytes contíguos realmente lidos.  
  
 `pdwUnreadable`  
 [out no] Retorna o número de bytes ilegíveis. Pode ser um valor nulo se o cliente tem interesse no número de bytes ilegíveis.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Se 100 bytes são solicitados a 50 primeiro são legíveis, os próximos 20 ilegível, e são 30 restantes são legíveis, esse método retorna:  
  
 *`pdwRead` = 50  
  
 *`pdwUnreadable` = 20  
  
 Nesse caso, porque `*pdwRead + *pdwUnreadable < dwCount`, o chamador deve fazer uma chamada adicional para ler os bytes restantes de 30 a 100 original solicitada e o [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objeto passado a `pStartContext` parâmetro deve ser adiantado por 70.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)