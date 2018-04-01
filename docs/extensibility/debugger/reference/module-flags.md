---
title: MODULE_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2dcd4b4d63942d7c2f94eda558ea491fa7a1e57e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="moduleflags"></a>MODULE_FLAGS
Usado para descrever um módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
typedef DWORD MODULE_FLAGS;  
```  
  
```csharp  
public enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
```  
  
## <a name="members"></a>Membros  
 MODULE_FLAG_NONE  
 Não especifica que nenhum módulo.  
  
 MODULE_FLAG_SYSTEM  
 Especifica um módulo do sistema.  
  
 MODULE_FLAG_SYMBOLS  
 Especifica um módulo de símbolo.  
  
 MODULE_FLAG_64BIT  
 Especifica um módulo de 64 bits.  
  
 MODULE_FLAG_OPTIMIZED  
 Especifica que o módulo foi otimizado. Esse estado é refletido no **módulos** janela.  
  
 MODULE_FLAG_UNOPTIMIZED  
 Especifica que o módulo não foi otimizado. Esse estado é refletido no **módulos** janela. Este é o estado padrão.  
  
## <a name="remarks"></a>Comentários  
 Usado para o `m_dwModuleFlags` membro o [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) estrutura.  
  
 Esses sinalizadores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)