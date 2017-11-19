---
title: IEnumDebugFrameInfo2::Next | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugFrameInfo2::Next
helpviewer_keywords: IEnumDebugFrameInfo2::Next
ms.assetid: 64a64eeb-5dea-4119-8a22-03771015d1e5
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f28025f93d23446a19fbca02c67d33c9a655a1d5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugframeinfo2next"></a>IEnumDebugFrameInfo2::Next
Retorna o próximo conjunto de elementos da enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Next(  
   ULONG       celt,  
   FRAMEINFO** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint        celt,  
   FRAMEINFO[] rgelt,  
   ref uint    pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 [in] O número de elementos para recuperar. Também especifica o tamanho máximo da `rgelt` matriz.  
  
 `rgelt`  
 [out no] Matriz de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) elementos devem ser preenchidos.  
  
 `pceltFetched`  
 [out] Retorna o número de elementos realmente retornados em `rgelt`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se menos do que o número solicitado de elementos podem ser retornados; caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)