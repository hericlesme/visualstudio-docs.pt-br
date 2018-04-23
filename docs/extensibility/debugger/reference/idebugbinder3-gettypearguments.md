---
title: IDebugBinder3::GetTypeArguments | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetTypeArguments
helpviewer_keywords:
- IDebugBinder3::GetTypeArguments method
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7f5e06b51cfea731d94cd0eb53d91b4dbdf6b471
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbinder3gettypearguments"></a>IDebugBinder3::GetTypeArguments
Esse método recupera uma lista de tipos de argumento associado a este objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetTypeArguments(  
   UINT          skip,  
   UINT          count,  
   IDebugField** ppFields,  
   UINT*         pFetched  
);  
```  
  
```csharp  
int GetTypeArguments(  
   uint          skip,  
   uint          count,  
   IDebugField[] ppFields,  
   out uint      pFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `skip`  
 [in] Número de campos a serem ignoradas antes de obter tipos de argumento.  
  
 `count`  
 [in] O número de campos de argumento para retornar (também especifica o tamanho do `ppFields` matriz).  
  
 `ppFields`  
 [out no] Uma matriz de campos que serão preenchidos no retorno deste método.  
  
 `pFetched`  
 [out] \(opcional) O número de argumento de tipo campos retornados na verdade.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O número de tipos de argumento pode ser obtido com antecedência com [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md).  
  
## <a name="see-also"></a>Consulte também  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)