---
title: IDebugFunctionObject::CreateObject | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugFunctionObject::CreateObject
helpviewer_keywords:
- IDebugFunctionObject::CreateObject method
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 15b41cc5ff9f60143cdbf006005358cb86eb7f30
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfunctionobjectcreateobject"></a>IDebugFunctionObject::CreateObject
Cria um objeto usando um construtor.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateObject(   
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   IDebugObject**        ppObject  
);  
```  
  
```csharp  
int CreateObject(  
   IDebugFunctionObject pConstructor,   
   uint                 dwArgs,   
   IDebugObject[]       pArgs,   
   out IDebugObject     ppObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pConstructor`  
 [in] Um [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objeto que representa o construtor do objeto a ser criado.  
  
 `dwArgs`  
 [in] O número de parâmetros na `pArg` matriz. Representa o número de parâmetros passados para o construtor.  
  
 `pArg`  
 [in] Uma matriz de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos que representam os parâmetros passados para o construtor.  
  
 `ppObject`  
 [out] Retorna um `IDebugObject` que representa o objeto recém-criado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Chame esse método para criar um objeto que representa uma instância de uma classe (ou outro tipo complexo que requer um construtor) que é um parâmetro para a função que é representado pelo [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface.  
  
 Se o parâmetro de objeto não tem um construtor, chame o [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)