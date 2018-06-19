---
title: IDebugMemoryContext2::GetInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugMemoryContext2::GetInfo method
ms.assetid: 08c7f091-1816-4d64-8834-f9ecaac5c58d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8cc0af2cfc56b22e2b6488056a73004d653431d9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122542"
---
# <a name="idebugmemorycontext2getinfo"></a>IDebugMemoryContext2::GetInfo
Recupera um [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) estrutura que descreve o contexto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetInfo(   
   CONTEXT_INFO_FIELDS dwFields,  
   CONTEXT_INFO*       pInfo  
);  
```  
  
```csharp  
int GetInfo(  
   enum_CONTEXT_INFO_FIELDS dwFields,   
   CONTEXT_INFO[]           pinfo  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFields`  
 [in] Uma combinação de sinalizadores do [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) enumeração que indicam quais campos do [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) estrutura devem ser preencher.  
  
 `pInfo`  
 [out no] O `CONTEXT_INFO` estrutura está preenchida.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)