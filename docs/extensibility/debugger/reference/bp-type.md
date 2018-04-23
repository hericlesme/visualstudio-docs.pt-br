---
title: BP_TYPE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_TYPE
helpviewer_keywords:
- BP_TYPE enumeration
ms.assetid: ef07191e-7966-43ab-96fb-1a0b1db3115d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 823b2b4bd53aabfdbcc887fe8ce4e1bf1bf858d7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="bptype"></a>BP_TYPE
Especifica se o ponto de interrupção estiver em um local de código, é um local de dados ou outro tipo de ponto de interrupção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_BP_TYPE {   
   BPT_NONE    = 0x0000,  
   BPT_CODE    = 0x0001,  
   BPT_DATA    = 0x0002,  
   BPT_SPECIAL = 0x0003  
};  
typedef DWORD BP_TYPE;  
```  
  
```csharp  
public enum enum_BP_TYPE {   
   BPT_NONE    = 0x0000,  
   BPT_CODE    = 0x0001,  
   BPT_DATA    = 0x0002,  
   BPT_SPECIAL = 0x0003  
};  
```  
  
## <a name="members"></a>Membros  
 BPT_NONE  
 Não especifica que nenhum tipo de ponto de interrupção.  
  
 BPT_CODE  
 Especifica um ponto de interrupção do código.  
  
 BPT_DATA  
 Especifica um ponto de interrupção de dados.  
  
 BPT_SPECIAL  
 Especifica um ponto de interrupção que não é um código nem um tipo de dados. Esse tipo foi preterido e não deve ser usado.  
  
## <a name="remarks"></a>Comentários  
 Passado como um parâmetro para o [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) e [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md) métodos.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)   
 [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)