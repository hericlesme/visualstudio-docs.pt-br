---
title: IDebugStackFrame2::GetExpressionContext | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 23aa07fee47645f50ed0e6d08efa9833d2487259
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121450"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
Obtém um contexto de avaliação para a avaliação da expressão no contexto atual de um quadro de pilhas e o thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetExpressionContext (   
   IDebugExpressionContext2** ppExprCxt  
);  
```  
  
```csharp  
int GetExpressionContext (   
   out IDebugExpressionContext2 ppExprCxt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppExprCxt`  
 [out] Retorna um [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) objeto que representa um contexto de avaliação da expressão.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Em geral, um contexto de avaliação de expressão pode ser pensado como um escopo para executar a avaliação da expressão. Chamar o [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método para analisar uma expressão e, em seguida, chamar resultante [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) métodos para avaliar a expressão analisada.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)