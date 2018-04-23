---
title: IDebugStackFrame2::GetDocumentContext | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetDocumentContext
helpviewer_keywords:
- IDebugStackFrame2::GetDocumentContext
ms.assetid: 69e81439-1238-4f18-9028-6fd1c1ba5e4a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14e7374fbea697b86d9ee838a6b8a76a57f920ff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugstackframe2getdocumentcontext"></a>IDebugStackFrame2::GetDocumentContext
Obtém o contexto de documento para este quadro de pilhas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetDocumentContext (   
   IDebugDocumentContext2** ppCxt  
);  
```  
  
```csharp  
int GetDocumentContext (   
   out IDebugDocumentContext2 ppCxt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppCxt`  
 [out] Retorna um [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) objeto que representa a posição atual em um documento de origem.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método é mais rápido do que chamar o [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) método e, em seguida, chamar o [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) método no contexto de código. No entanto, não há garantia de que cada mecanismo de depuração (DE) implementar esse método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)