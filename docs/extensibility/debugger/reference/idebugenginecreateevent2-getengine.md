---
title: IDebugEngineCreateEvent2::GetEngine | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineCreateEvent2::GetEngine
helpviewer_keywords:
- IDebugEngineCreateEvent2::GetEngine
ms.assetid: 187d24ed-9f9a-4418-a0ef-b8a19f54652c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cea15ed51cfcd81c208ef73e359058711bfdc5c0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31110485"
---
# <a name="idebugenginecreateevent2getengine"></a>IDebugEngineCreateEvent2::GetEngine
Recupera o objeto que representa o mecanismo de depuração recém-criado (DE).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetEngine(   
   IDebugEngine2** pEngine  
);  
```  
  
```csharp  
int GetEngine(   
   out IDebugEngine2 pEngine  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pEngine`  
 [out] Retorna um [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) objeto que representa o DE recém-criado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)