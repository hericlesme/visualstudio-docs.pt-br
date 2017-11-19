---
title: IEnumDebugThreads2::Next | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugThreads2::Next
helpviewer_keywords: IEnumDebugThreads2::Next
ms.assetid: bcffd954-3c67-4867-96f3-041ddb3e34d4
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a12c6232f135e8bf4569b6de90a7191548e28746
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugthreads2next"></a>IEnumDebugThreads2::Next
Retorna o próximo conjunto de elementos da enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Next(  
   ULONG           celt,  
   IDebugThread2** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint            celt,  
   IDebugThread2[] rgelt,  
   ref uint        pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 [in] O número de elementos para recuperar. Também especifica o tamanho máximo da `rgelt` matriz.  
  
 `rgelt`  
 [out no] Matriz de [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) elementos devem ser preenchidos.  
  
 `pceltFetched`  
 [out] Retorna o número de elementos realmente retornados em `rgelt`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se menos do que o número solicitado de elementos podem ser retornados; caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)