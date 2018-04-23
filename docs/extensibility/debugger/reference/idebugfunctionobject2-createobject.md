---
title: IDebugFunctionObject2::CreateObject | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c5283d72972e1ba579cafa82648cbf0ec0fcf80c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Cria um objeto que usa um construtor que recebe as configurações de sinalizador de avaliação e um valor de tempo limite.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateObject (  
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugObject**        ppObject  
);  
```  
  
```csharp  
int CreateObject (  
   IDebugFunctionObject pConstructor,  
   uint                 dwArgs,  
   IDebugObject[]       pArgs,  
   uint                 dwEvalFlags,  
   uint                 dwTimeout,  
   out IDebugObject**   ppObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pConstructor`  
 [in] Um [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objeto que representa o construtor do objeto a ser criado.  
  
 `dwArgs`  
 [in] O número de parâmetros na `pArg` matriz. Representa o número de parâmetros passados para o construtor.  
  
 `pArgs`  
 [in] Uma matriz de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos que representa os parâmetros passados para o construtor.  
  
 `dwEvalFlags`  
 [in] Uma combinação de sinalizadores do [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) enumeração que especificam como a avaliação deve ser executada.  
  
 `dwTimeout`  
 [in] Tempo máximo, em milissegundos, de espera antes de retornar desse método. Use **infinito** aguardar indefinidamente.  
  
 `ppObject`  
 [out] Retorna um **IDebugObject** que representa o objeto recém-criado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Chame este método para criar um objeto que representa uma instância de uma classe ou outro tipo complexo que requer um construtor, que é um parâmetro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)