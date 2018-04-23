---
title: STEPKIND | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- STEPKIND
helpviewer_keywords:
- STEPKIND enumeration
ms.assetid: d3d8cf76-24bf-455e-803e-0e3e28f0b262
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 38f28748914566162cbe070dd3d2e606eb8ce118
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="stepkind"></a>STEPKIND
Especifica o tipo de etapa de revisão.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
typedef DWORD STEPKIND;  
```  
  
```csharp  
public enum enum_STEPKIND {   
   STEP_INTO      = 0,  
   STEP_OVER      = 1,  
   STEP_OUT       = 2,  
   STEP_BACKWARDS = 3  
};  
```  
  
## <a name="members"></a>Membros  
 STEP_INTO  
 Etapas em uma função.  
  
 STEP_OVER  
 Etapas em uma função.  
  
 STEP_OUT  
 Etapas de uma função.  
  
 STEP_BACKWARDS  
 Etapas com versões anteriores em uma função.  
  
## <a name="remarks"></a>Comentários  
 Passado como um argumento para o [etapa](../../../extensibility/debugger/reference/idebugprocess3-step.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)