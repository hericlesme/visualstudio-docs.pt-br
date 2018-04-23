---
title: IDebugEngine2::RemoveAllSetExceptions | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e3446b910aa1e728319d0f4c7acdbf65b01d1cb4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
Remove a lista de exceções que definiu o IDE para um idioma ou a arquitetura de tempo de execução específica.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT RemoveAllSetExceptions(   
   REFGUID guidType  
);  
```  
  
```csharp  
int RemoveAllSetExceptions(   
   ref Guid guidType  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `guidType`  
 [in] O GUID para o idioma ou o GUID para o mecanismo de depuração que é específico para uma arquitetura de tempo de execução.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 As exceções removidas por este método foram definidas por chamadas anteriores para o [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) método.  
  
 Para remover uma exceção específica, chame o [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)