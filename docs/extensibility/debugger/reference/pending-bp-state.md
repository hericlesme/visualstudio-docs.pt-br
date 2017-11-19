---
title: PENDING_BP_STATE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PENDING_BP_STATE
helpviewer_keywords: PENDING_BP_STATE enumeration
ms.assetid: ac04ad72-fa92-4a15-ade2-0d0bbbadfc7f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: de7ac105f7dea0c57297c29a4bdb8d5c85f62321
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="pendingbpstate"></a>PENDING_BP_STATE
Especifica o estado de um ponto de interrupção pendente (um ponto de interrupção que ainda não foi vinculado).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_PENDING_BP_STATE {   
   PBPS_NONE     = 0x0000,  
   PBPS_DELETED  = 0x0001,  
   PBPS_DISABLED = 0x0002,  
   PBPS_ENABLED  = 0x0003  
};  
typedef DWORD PENDING_BP_STATE;  
```  
  
```csharp  
public enum enum_PENDING_BP_STATE {   
   PBPS_NONE     = 0x0000,  
   PBPS_DELETED  = 0x0001,  
   PBPS_DISABLED = 0x0002,  
   PBPS_ENABLED  = 0x0003  
};  
```  
  
## <a name="members"></a>Membros  
 PBPS_NONE  
 Espaço reservado para zero. Esse valor nunca é retornado.  
  
 PBPS_DELETED  
 Indica que o ponto de interrupção pendente foi excluído.  
  
 PBPS_DISABLED  
 Indica que o ponto de interrupção pendente está desabilitado.  
  
 PBPS_ENABLED  
 Indica que o ponto de interrupção pendente está habilitado.  
  
## <a name="remarks"></a>Comentários  
 Usar como o `state` membro o [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) estrutura.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)