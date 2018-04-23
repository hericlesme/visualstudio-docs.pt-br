---
title: IDebugExpressionEvaluationCompleteEvent2::GetResult | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
ms.assetid: d9ad3e22-b6b2-421e-9a43-6bb8c70d12a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 92496965fe463df4343d51b07819c073de163368
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpressionevaluationcompleteevent2getresult"></a>IDebugExpressionEvaluationCompleteEvent2::GetResult
Obtém o resultado da avaliação de expressão.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetResult(   
   IDebugProperty2** ppResult  
);  
```  
  
```csharp  
int GetResult(   
   out IDebugProperty2 ppResult  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppResult`  
 [out] Retorna um [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto que representa o resultado da avaliação de expressão.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Retornado [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto contém o valor da expressão avaliada. Observe que esse valor pode ser um valor complexo, como uma matriz, mas o resultado final deve ser um numérico ou valor que é exibido para o usuário de cadeia de caracteres.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)