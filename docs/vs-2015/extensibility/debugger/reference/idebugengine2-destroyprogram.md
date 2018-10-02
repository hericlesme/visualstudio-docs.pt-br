---
title: IDebugEngine2::DestroyProgram | Microsoft Docs
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
- IDebugEngine2::DestroyProgram
helpviewer_keywords:
- IDebugEngine2::DestroyProgram
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9e6ce448ec0722d06ef17d70a66f9f32610a354b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464010"
---
# <a name="idebugengine2destroyprogram"></a>IDebugEngine2::DestroyProgram
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugEngine2::DestroyProgram](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugengine2-destroyprogram).  
  
Informa um mecanismo de depuração (DES) que o programa especificado foi encerrado atypically e que o DE deve limpar todas as referências para o programa e enviar um programa destruir o evento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT DestroyProgram(   
   IDebugProgram2* pProgram  
);  
```  
  
```cpp#  
int DestroyProgram(   
   IDebugProgram2 pProgram  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pProgram`  
 [in] Uma [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa o programa que atypically foi encerrado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Depois que esse método é chamado, o DE subsequentemente envia uma [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) eventos de volta para o Gerenciador de sessão de depuração (SDM).  
  
 Esse método não está implementado (retorna `E_NOTIMPL`) se a Alemanha é executado no mesmo processo que o programa que está sendo depurado. Esse método é implementado somente se a Alemanha é executado no mesmo processo que o SDM.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

