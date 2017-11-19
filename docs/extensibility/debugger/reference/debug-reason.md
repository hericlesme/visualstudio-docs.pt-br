---
title: DEBUG_REASON | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DEBUG_REASON
helpviewer_keywords: DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9607afd765e1ddbc9fb2be97a0b7694aed7d493d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="debugreason"></a>DEBUG_REASON
Especifica o motivo pelo qual o processo foi iniciado para depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
typedef DWORD DEBUG_REASON;  
```  
  
```csharp  
public enum enum_DEBUG_REASON {  
   DEBUG_REASON_ERROR         = 0,  
   DEBUG_REASON_USER_LAUNCHED = 1,  
   DEBUG_REASON_USER_ATTACHED = 2,  
   DEBUG_REASON_AUTO_ATTACHED = 3,  
   DEBUG_REASON_CAUSALITY     = 4  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 DEBUG_REASON_ERROR  
 Ocorreu um erro não específico (isto é usado como uma condição padrão quando nenhuma das outras razões de ajuste).  
  
 DEBUG_REASON_USER_LAUNCHED  
 O processo foi iniciado por solicitação do usuário.  
  
 DEBUG_REASON_USER_ATTACHED  
 O processo de execução já foi anexado pelo usuário.  
  
 DEBUG_REASON_AUTO_ATTACHED  
 O processo foi anexado automaticamente ao quando ele foi iniciado.  
  
 DEBUG_REASON_CAUSALITY  
 O processo foi iniciado devido a um *Just-In-Time* eventos de depuração (JIT).  
  
## <a name="remarks"></a>Comentários  
 Retornado do [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)