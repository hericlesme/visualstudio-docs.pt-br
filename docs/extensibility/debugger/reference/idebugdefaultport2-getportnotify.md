---
title: IDebugDefaultPort2::GetPortNotify | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDefaultPort2::GetPortNotify
helpviewer_keywords:
- IDebugDefaultPort2::GetPortNotify
ms.assetid: 3ae715ee-9886-4694-a52b-59bb3b27467a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eca2893f388c4dabb244d042d652d3ab604d88bf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103277"
---
# <a name="idebugdefaultport2getportnotify"></a>IDebugDefaultPort2::GetPortNotify
Esse método obtém um [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interface para essa porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetPortNotify(  
   IDebugPortNotify2** ppPortNotify  
);  
```  
  
```csharp  
int GetPortNotify(  
   out IDebugPortNotify2 ppPortNotify  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppPortNotify`  
 [out] Um [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Normalmente, o `QueryInterface` método é chamado no objeto que implementa o [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interface para obter uma [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) interface. No entanto, há circunstâncias em que a interface desejada é implementada em um objeto diferente. Este método oculta nessas circunstâncias e retorna o `IDebugPortNotify2` interface do objeto mais apropriado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)