---
title: IDebugQueryEngine2::GetEngineInterface | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
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
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b3838155ba819a332c4b984432a19154509d7b88
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47472952"
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugQueryEngine2::GetEngineInterface](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugqueryengine2-getengineinterface).  
  
Obtém uma interface de (DES) do mecanismo de depuração personalizado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
 [out] Retorna um `IUnknown` objeto representa o mecanismo de depuração (DE) e que pode ser consultado para qualquer outra interface válido associado com a DE (por exemplo [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) ou [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)).  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A interface resultante deve ser usada com cuidado porque chamar por meio de interfaces recuperados desse método contorna o processamento do Gerenciador de depuração de sessão e pode resultar no SDM entrar em um estado inválido ou gerando erros durante a depuração.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)

