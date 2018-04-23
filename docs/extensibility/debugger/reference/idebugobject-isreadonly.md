---
title: IDebugObject::IsReadOnly | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 84cac5c66dd20dc9641fee7f05b456b25cbe2ffc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
Determina se este objeto é somente leitura.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT IsReadOnly(   
   BOOL* pfIsReadOnly  
);  
```  
  
```csharp  
int IsReadOnly(  
   out int pfIsReadOnly  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pfIsReadOnly`  
 [out] Retorna diferente de zero (`TRUE`) se este objeto é somente leitura; caso contrário, retorna zero (`FALSE`).  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Um objeto somente leitura não pode ter seu valor alterado depois que ela é criada.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)