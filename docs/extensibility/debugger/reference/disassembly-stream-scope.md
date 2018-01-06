---
title: DISASSEMBLY_STREAM_SCOPE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords: DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ff793f5d84b21d6c521a3b70b1a553177c95f75c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="disassemblystreamscope"></a>DISASSEMBLY_STREAM_SCOPE
Especifica o escopo do fluxo de desmontagem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
typedef DWORD DISASSEMBLY_STREAM_SCOPE;  
```  
  
```csharp  
public enum enum_DISASSEMBLY_STREAM_SCOPE {   
   DSS_HUGE     = 0x10000000,  
   DSS_FUNCTION = 0x0001,  
   DSS_MODULE   = (DSS_HUGE) | 0x0002,  
   DSS_ALL      = (DSS_HUGE) | 0x0003  
};  
```  
  
## <a name="members"></a>Membros  
 DSS_HUGE  
 Especifica que desmontar o contexto de código poderia gerar saída de mais de um cliente normalmente deseja recuperar em uma única chamada.  
  
 DSS_FUNCTION  
 Especifica que a função contida pelo contexto de código deve ser desmontada. Especifica que o fluxo de desmontagem representa uma função, quando retornado pelo [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) método.  
  
 DSS_MODULE  
 Quando retornado pelo `IDebugDisassemblyStream2::GetScope` método, especifica que o fluxo de desmontagem representa um módulo.  
  
 DSS_ALL  
 Especifica a desmontagem para o espaço de endereço inteiro.  
  
## <a name="remarks"></a>Comentários  
 Passado como um argumento para o [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) método e retornado pelo [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) método.  
  
 Esses valores podem ser combinados com um bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)