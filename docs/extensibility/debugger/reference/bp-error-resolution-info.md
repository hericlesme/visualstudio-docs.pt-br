---
title: BP_ERROR_RESOLUTION_INFO | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9fdf3b6aee272990fb22feee13f8e46ee8550073
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102129"
---
# <a name="bperrorresolutioninfo"></a>BP_ERROR_RESOLUTION_INFO
Descreve a resolução de um ponto de interrupção de erro, inclusive local, o programa e o thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct _BP_ERROR_RESOLUTION_INFO {   
   BPERESI_FIELDS         dwFields;  
   BP_RESOLUTION_LOCATION bpResLocation;  
   IDebugProgram2*        pProgram;  
   IDebugThread2*         pThread;  
   BSTR                   bstrMessage;  
   BP_ERROR_TYPE          dwType;  
} BP_ERROR_RESOLUTION_INFO;  
```  
  
```csharp  
public struct BP_ERROR_RESOLUTION_INFO {   
   public uint                   dwFields;  
   public BP_RESOLUTION_LOCATION bpResLocation;  
   public IDebugProgram2         pProgram;  
   public IDebugThread2          pThread;  
   public string                 bstrMessage;  
   public uint                   dwType;  
};  
```  
  
## <a name="members"></a>Membros  
 `dwFields`  
 Uma combinação de valores da [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) enumeração que especifica quais campos dessa estrutura são preenchidos.  
  
 `bpResLocation`  
 O [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) union, que especifica o local de resolução do ponto de interrupção.  
  
 `pProgram`  
 O [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa o aplicativo no qual ocorreu o erro de ponto de interrupção.  
  
 `pThread`  
 O [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa o thread que está executando o aplicativo que gerou o erro de ponto de interrupção.  
  
 `bstrMessage`  
 Uma cadeia de caracteres que contém qualquer mensagem de aviso ou erro resultantes da resolução erro.  
  
 `dwType`  
 Um valor da [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) enumeração que especifica o tipo de erro do ponto de interrupção.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é retornada a partir de [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)   
 [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)