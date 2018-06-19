---
title: IDebugDisassemblyStream2::GetScope | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::GetScope
helpviewer_keywords:
- IDebugDisassemblyStream2::GetScope
ms.assetid: 71c6e632-642a-42d8-a995-77e4ac190a5b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1a155c521370670ecf141177a29f70e67d812d68
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105965"
---
# <a name="idebugdisassemblystream2getscope"></a>IDebugDisassemblyStream2::GetScope
Obtém o escopo do fluxo de desmontagem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetScope(   
   DISASSEMBLY_STREAM_SCOPE* pdwScope  
);  
```  
  
```csharp  
int GetScope(   
   out enum_ DISASSEMBLY_STREAM_SCOPE pdwScope  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwScope`  
 [out] Retorna um valor da [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) enumeração que descreve o escopo deste fluxo de desmontagem.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O escopo de uma desmontagem pode ser uma função ou o módulo inteiro, por exemplo.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)