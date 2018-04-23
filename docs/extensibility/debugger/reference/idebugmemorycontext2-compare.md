---
title: IDebugMemoryContext2::Compare | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b9c72120a4153ed6d0d19a2cf2b7d3a9a9943801
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Compara o contexto de memória para cada contexto na matriz fornecida da maneira indicado pelos sinalizadores de comparação, retornando um índice do primeiro contexto correspondente.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Compare(   
   CONTEXT_COMPARE        compare,  
   IDebugMemoryContext2** rgpMemoryContextSet,  
   DWORD                  dwMemoryContextSetLen,  
   DWORD*                 pdwMemoryContext  
);  
```  
  
```csharp  
int Compare(  
   enum_CONTEXT_COMPARE   compare,   
   IDebugMemoryContext2[] rgpMemoryContextSet,   
   uint                   dwMemoryContextSetLen,   
   out uint               pdwMemoryContext  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `compare`  
 [in] Um valor da [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) enumeração que determina o tipo de comparação.  
  
 `rgpMemoryContextSet`  
 [in] Uma matriz de referências para o [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objetos para comparação.  
  
 `dwMemoryContextSetLen`  
 [in] O número de contextos no `rgpMemoryContextSet` matriz.  
  
 `pdwMemoryContext`  
 [out] Retorna o índice do primeiro contexto de memória que satisfaz a comparação.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro. Retorna `E_COMPARE_CANNOT_COMPARE` se os dois contextos não podem ser comparados.  
  
## <a name="remarks"></a>Comentários  
 Não tem um mecanismo de depuração (DE) para dar suporte a todos os tipos de comparações, mas ele deve dar suporte ao menos `CONTEXT_EQUAL`, `CONTEXT_LESS_THAN`, `CONTEXT_GREATER_THAN` e `CONTEXT_SAME_SCOPE`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)