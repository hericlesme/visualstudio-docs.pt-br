---
title: IDebugExpressionEvaluator2::SetIDebugIDECallback | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetIDebugIDECallback
- SetIDebugIDECallback
ms.assetid: f01c40ad-ef4b-477b-8304-602c6972bc88
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e49928e984a3981e0a30d396aaefafe9ce7db574
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
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