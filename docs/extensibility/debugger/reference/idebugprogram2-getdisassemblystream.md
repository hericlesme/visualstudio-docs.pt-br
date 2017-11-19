---
title: IDebugProgram2::GetDisassemblyStream | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::GetDisassemblyStream
helpviewer_keywords: IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b623b7936516a581037cf01bfc7a92e11d38415f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
Obtém o fluxo de desmontagem para este programa ou uma parte desse programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetDisassemblyStream(   
   DISASSEMBLY_STREAM_SCOPE   dwScope,  
   IDebugCodeContext2*        pCodeContext,  
   IDebugDisassemblyStream2** ppDisassemblyStream  
);  
```  
  
```csharp  
int GetDisassemblyStream(   
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,  
   IDebugCodeContext2             pCodeContext,  
   out IDebugDisassemblyStream2   ppDisassemblyStream  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwScope`  
 [in] Especifica um valor a partir de [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) enumeração que define o escopo do fluxo de desmontagem.  
  
 `pCodeContext`  
 [in] Um [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que representa a posição em que iniciar o fluxo de desmontagem.  
  
 `ppDisassemblyStream`  
 [out] Retorna um [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) objeto que representa o fluxo de desmontagem.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro. Retorna `E_DISASM_NOTSUPPORTED` se a desmontagem não há suporte para essa arquitetura específica.  
  
## <a name="remarks"></a>Comentários  
 Se o `dwScopes` parâmetro tem o `DSS_HUGE` sinalizador do [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) enumeração definida e, em seguida, a desmontagem deve retornar um grande número de instruções de desmontagem, por exemplo, um arquivo inteiro ou módulo. Se o `DSS_HUGE` sinalizador não estiver definido, a desmontagem deve ser restrita a uma região de pequena, geralmente que de uma única função.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)