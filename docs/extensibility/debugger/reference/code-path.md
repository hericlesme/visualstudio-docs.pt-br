---
title: CODE_PATH | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CODE_PATH
helpviewer_keywords:
- CODE_PATH structure
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6c88737638b20eafdef0ef84f5c45e494cf39607
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109775"
---
# <a name="codepath"></a>CODE_PATH
Descreve uma chamada de método ou função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef struct tagCODE_PATH {   
   BSTR                bstrName;  
   IDebugCodeContext2* pCode;  
} CODE_PATH;  
```  
  
```csharp  
public struct CODE_PATH {  
   public string            bstrName;  
   public IDebugCodeContext pCode;  
}  
```  
  
## <a name="members"></a>Membros  
 bstrName  
 O nome do caminho de código.  
  
 pCode  
 O [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto identifica onde no código para entrar em uma função.  
  
## <a name="remarks"></a>Comentários  
 Essa estrutura é usada para implementar a entrar em uma função. [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) retorna todas as chamadas do local atual no programa que está sendo depurado. Esta estrutura representa um essa chamada.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)