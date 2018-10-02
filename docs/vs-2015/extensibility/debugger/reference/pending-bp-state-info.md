---
title: PENDING_BP_STATE_INFO | Microsoft Docs
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
- PENDING_BP_STATE_INFO
helpviewer_keywords:
- PENDING_BP_STATE_INFO structure
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 77151825f1e241110a0af1fece80f34ea39fd331
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47472746"
---
# <a name="pendingbpstateinfo"></a>PENDING_BP_STATE_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [PENDING_BP_STATE_INFO](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/pending-bp-state-info).  
  
Contém informações sobre o estado de um ponto de interrupção que está pronto para associar a um local de código.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
typedef struct _tagPENDING_BP_STATE_INFO {   
   PENDING_BP_STATE       state;  
   PENDING_BP_STATE_FLAGS flags;  
} PENDING_BP_STATE_INFO;  
```  
  
```csharp  
public struct PENDING_BP_STATE_INFO {   
   public uint state;  
   public uint flags;  
};  
```  
  
## <a name="members"></a>Membros  
 estado  
 Um valor a partir de [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) enumeração que especifica o estado do ponto de interrupção pendente.  
  
 sinalizadores  
 Uma combinação de sinalizadores do [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) enumeração que especifica se o ponto de interrupção é virtualizado.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é passada para o [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md) método onde ele é preenchido.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)   
 [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)   
 [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)

