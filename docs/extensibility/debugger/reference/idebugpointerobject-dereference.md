---
title: IDebugPointerObject::Dereference | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4cc287887baf2530786b03b591d6c03592055e55
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31113020"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Obtém o objeto apontado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT DeReference(   
   DWORD          dwIndex,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Dereference(  
   uint             dwIndex,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwIndex`  
 [in] Um deslocamento de byte simples desde o início do objeto apontado.  
  
 `ppObject`  
 [out] Retorna um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) do objeto que representa o objeto apontado, além de deslocamento, se houver.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro. Retornará E_FAIL se este objeto não aponta para um outro objeto.  
  
## <a name="remarks"></a>Comentários  
 O objeto apontado pode ser um primitivo ou um tipo mais complexo, como uma classe ou estrutura.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)