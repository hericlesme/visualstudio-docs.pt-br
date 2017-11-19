---
title: IDebugThread2::SetThreadName | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugThread2::SetThreadName
helpviewer_keywords: IDebugThread2::SetThreadName
ms.assetid: fa934121-3f58-44dc-9c30-d3f752e44c8b
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fd32ebe91a1a88da1d33bba37ae56084fc48b891
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugthread2setthreadname"></a>IDebugThread2::SetThreadName
Define o nome do thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetThreadName (   
   LPCOLESTR pszName  
);  
```  
  
```csharp  
int SetThreadName (   
   string pszName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszName`  
 [in] O nome do thread.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Para obter o nome de thread, chame o [GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)