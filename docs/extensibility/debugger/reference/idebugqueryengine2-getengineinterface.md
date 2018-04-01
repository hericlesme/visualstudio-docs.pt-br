---
title: IDebugQueryEngine2::GetEngineInterface | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 65f40bf3e0e110a6d945921d06443f0c8a608d20
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
Obtém uma interface de mecanismo (DE) personalizados de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetEngineInterface(   
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetEngineInterface(   
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppUnk`  
 [out] Retorna um `IUnknown` objeto representa o mecanismo de depuração (DE) e que pode ser consultado para qualquer outra interface válido associado com um DE (por exemplo [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) ou [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)).  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A interface resultante deve ser usada com cuidado porque chamar por meio das interfaces recuperados deste método contorna a processamento do Gerenciador de depuração de sessão e pode resultar em SDM entrar em um estado inválido ou gerar erros durante a depuração.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)