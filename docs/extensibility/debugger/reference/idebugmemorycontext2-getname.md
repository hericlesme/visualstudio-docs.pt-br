---
title: IDebugMemoryContext2::GetName | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMemoryContext2::GetName
helpviewer_keywords:
- IDebugMemoryContext2::GetName method
- GetName method
ms.assetid: 8c212556-7d9e-4d68-b2a9-8212f50d0287
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cbe610430239936e1722df74960651659a92947c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmemorycontext2getname"></a>IDebugMemoryContext2::GetName
Recupera o nome de exibição de usuário para este contexto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetName(   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetName(  
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstrName`  
 [out] Retorna o nome do contexto da memória.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O nome de um contexto de memória não é usado normalmente.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)