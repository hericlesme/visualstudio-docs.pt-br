---
title: IDebugProgramNode2::Attach_V7 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7db57be153634476b8c0ba5ff6b6b1273ef190be
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2018
---
# <a name="idebugprogramnode2attachv7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> DEPRECATED. NÃO USE.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Attach_V7 (
   IDebugProgram2*       pMDMProgram,
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason
);
```

```csharp
int Attach_V7 (
   IDebugProgram2       pMDMProgram,
   IDebugEventCallback2 pCallback,
   uint                 dwReason
);
```

#### <a name="parameters"></a>Parâmetros

`pMDMProgram` [in] O [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa o programa para anexar a interface.

 `pCallback` [in] O [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) interface a ser usada para enviar eventos de depuração para o SDM.

 `dwReason` [in] Um valor da [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) enumeração que especifica o motivo para anexar.

## <a name="return-value"></a>Valor de retorno

Uma implementação deve retornar sempre `E_NOTIMPL`.

## <a name="remarks"></a>Comentários

> [!WARNING]
> A partir do Visual Studio 2005, esse método não é mais usado e deve retornar sempre `E_NOTIMPL`. Consulte o [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interface para uma abordagem alternativa, se o nó de programa precisa indicar que ele não pode ser conectado ou se o nó do programa é simplesmente definir o programa `GUID`. Caso contrário, implementar a [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método.

## <a name="prior-to-visual-studio-2005"></a>Antes do Visual Studio 2005

Esse método deve ser implementada somente se o DE é executado no espaço de endereço do programa que está sendo depurado. Caso contrário, esse método deve retornar `S_FALSE`.

Quando este método é chamado, o DE deve enviar o [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) objeto de evento, se ele já não tiver sido enviado para esta instância do [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interface, bem como a [ IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) e [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) objetos de evento. O [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) o objeto de evento é enviado se o `dwReason` parâmetro é `ATTACH_REASON_LAUNCH`.

Deve chamar o do [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) método no [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto fornecido pelo [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) eventos de objeto e deve armazenar o GUID do programa nos dados da instância para o `IDebugProgram2` objeto implementado por DE.

## <a name="see-also"></a>Consulte também

[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)  
[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)  
[Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md)  
[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)  
[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)  
[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)  
[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)  
[ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)