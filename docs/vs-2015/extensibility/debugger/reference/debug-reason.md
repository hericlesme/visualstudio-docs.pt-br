---
title: DEBUG_REASON | Microsoft Docs
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
- DEBUG_REASON
helpviewer_keywords:
- DEBUG_REASON enumeration
ms.assetid: ad2ee898-8648-4671-9078-d32873862346
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 883630e7c9e00a58eac143a6cde7ee40109bb4e9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47476284"
---
# <a name="debugreason"></a>DEBUG_REASON
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [DEBUG_REASON](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/debug-reason).  
  
Especifica por que o processo foi iniciado para depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
 Ocorreu um erro não específico (Isso é usado como uma condição padrão quando nenhuma das outras questões de ajuste).  
  
 DEBUG_REASON_USER_LAUNCHED  
 O processo foi iniciado mediante solicitação do usuário.  
  
 DEBUG_REASON_USER_ATTACHED  
 O processo de execução já foi anexado pelo usuário.  
  
 DEBUG_REASON_AUTO_ATTACHED  
 O processo foi anexado automaticamente a quando ele foi iniciado.  
  
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

