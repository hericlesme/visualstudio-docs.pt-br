---
title: IDebugExpressionEvaluator::SetRegistryRoot | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot
helpviewer_keywords:
- IDebugExpressionEvaluator::SetRegistryRoot method
ms.assetid: 790886d8-1975-4d3c-9a75-cd86c1faf4ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 70b1730fc44deeb7e32433480f02f750c9bec193
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpressionevaluatorsetregistryroot"></a>IDebugExpressionEvaluator::SetRegistryRoot
Esse método define a raiz do registro. Usado para depuração lado a lado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetRegistryRoot (   
   LPCOLESTR ustrRegistryRoot  
);  
```  
  
```csharp  
int SetRegistryRoot(  
   string ustrRegistryRoot  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ustrRegistryRoot`  
 [in] A raiz do registro novo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A raiz do registro especificado normalmente é definida quando o avaliador de expressão é criado pela primeira vez e aponta para a chave do registro para uma versão específica do Visual Studio (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*x. y* , onde *x. y* é um número de versão).  
  
## <a name="see-also"></a>Consulte também  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)