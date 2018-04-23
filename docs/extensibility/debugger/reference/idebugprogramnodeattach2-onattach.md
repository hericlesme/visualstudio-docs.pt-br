---
title: IDebugProgramNodeAttach2::OnAttach | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3c7c7e6f7ef640b192b7ed8c57ac87375a5ad189
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Anexa ao programa associado ou adia o processo de conexão para o [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT OnAttach(  
   [in] REFGUID guidProgramId  
);  
```  
  
```csharp  
int OnAttach(  
   ref Guid guidProgramId  
};  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `guidProgramId`  
 [in] `GUID` para atribuir ao programa associado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se o [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método não deve ser chamado. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Este método é chamado durante o processo de conexão, antes de [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método é chamado. O `OnAttach` método pode executar o processo de conexão (nesse caso, este método retorna `S_FALSE`) ou adiar o processo de conexão para o `IDebugEngine2::Attach` método (o `OnAttach` retorna método `S_OK`). Em ambos os casos, o `OnAttach` método pode definir o `GUID` do programa que está sendo depurado a determinado `GUID`.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md)