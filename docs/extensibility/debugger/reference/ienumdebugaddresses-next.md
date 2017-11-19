---
title: IEnumDebugAddresses::Next | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugAddresses::Next
helpviewer_keywords: IEnumDebugAddresses::Next method
ms.assetid: 941e4be7-858d-433a-9259-18d0d017be9e
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 056c0f54f6e9d00f76674fa98542835c6d4930a7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugaddressesnext"></a>IEnumDebugAddresses::Next
Esse método retorna o próximo conjunto de elementos da enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Next(  
   ULONG           celt,  
   IDebugAddress** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint            celt,  
   IDebugAddress[] rgelt,  
   ref uint        pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 [in] O número de elementos para recuperar. Também especifica o tamanho máximo da `rgelt` matriz.  
  
 `rgelt`  
 [out no] Matriz de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) elementos devem ser preenchidos.  
  
 `pceltFetched`  
 [out] Retorna o número de elementos realmente retornados em `rgelt`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se menos do que o número solicitado de elementos podem ser retornados; caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)