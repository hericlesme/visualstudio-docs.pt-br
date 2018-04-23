---
title: IEnumDebugCodeContexts2::Reset | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugCodeContexts2::Reset
helpviewer_keywords:
- IEnumDebugCodeContexts2::Reset
ms.assetid: df6cf1e3-2ef8-4d38-81a0-8e9adf151884
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6db487e60215416813dcc67647241fe4684512c0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugcodecontexts2reset"></a>IEnumDebugCodeContexts2::Reset
Redefine a enumeração para o primeiro elemento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Depois que este método é chamado, a próxima chamada para o [próximo](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md) método retorna o primeiro elemento da enumeração.  
  
## <a name="see-also"></a>Consulte também  
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)