---
title: BPRESI_FIELDS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1b6ecfd729762944bcf26814e735c4c73841e2d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="bpresifields"></a>BPRESI_FIELDS
Especifica as informações a serem recuperados sobre a resolução bem-sucedida de um ponto de interrupção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
typedef DWORD BPRESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
```  
  
## <a name="members"></a>Membros  
 BPRESI_BPRESLOCATION  
 Inicializar/usar o `bpResLocation` campo (localização de resolução do ponto de interrupção) do [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) estrutura.  
  
 BPRESI_PROGRAM  
 Inicializar/usar o `pProgram` campo o `BP_RESOLUTION_INFO` estrutura.  
  
 BPRESI_THREAD  
 Inicializar/usar o `pThread` campo o `BP_RESOLUTION_INFO` estrutura.  
  
 BPRESI_ALLFIELDS  
 Especifica todos os campos.  
  
## <a name="remarks"></a>Comentários  
 Passado para o [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) método para indicar quais campos do [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) estrutura devem ser inicializado.  
  
 Esses sinalizadores também são usados para indicar quais campos do `BP_RESOLUTION_INFO` estrutura são válidos e usadas quando essa estrutura é retornada.  
  
 Esses valores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)