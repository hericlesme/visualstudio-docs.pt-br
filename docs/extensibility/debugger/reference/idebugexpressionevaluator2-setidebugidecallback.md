---
title: IDebugExpressionEvaluator2::SetIDebugIDECallback | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetIDebugIDECallback
- SetIDebugIDECallback
ms.assetid: f01c40ad-ef4b-477b-8304-602c6972bc88
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b272a7db4bfc5c7405493759d5e9c1864eaaa07d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpressionevaluator2setidebugidecallback"></a>IDebugExpressionEvaluator2::SetIDebugIDECallback
Permite que um mecanismo de depuração passar um retorno de chamada para o avaliador de expressão durante a inicialização.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetIDebugIDECallback (  
   IDebugIDECallback * pCallback  
);  
```  
  
```csharp  
int SetIDebugIDECallback (  
   IDebugIDECallback pCallback  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pCallback`  
 [in] Interface para o retorno de chamada.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)