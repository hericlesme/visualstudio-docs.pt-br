---
title: Eventos de controle | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 40e07e480a89629da919af9d6542b2879c49718f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="control-events"></a>Eventos de controle
Você deve enviar eventos durante a execução controlada de seu programa. Todos os eventos são enviados usando a [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) de interface e ter atributos que exigem que você implemente o [IDebugEvent2::GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) método.  
  
## <a name="additional-methods"></a>Métodos adicionais  
 Alguns eventos exigem a implementação de métodos adicionais, como segue:  
  
-   Enviando o [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interface quando o mecanismo de depuração (DE) é inicializado exige que você implemente o [IDebugEngineCreateEvent2::GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) método.  
  
-   Controle de execução requer a implementação de eventos de controle, como o [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) e[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interfaces. **IDebugBreakEvent2** é necessária somente para as quebras de assíncronas.  
  
-   Passo a passo funções requer a implementação do [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interface e seus métodos.  
  
 Eventos derivando de pontos de interrupção exigem a implementação do [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), e [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) interfaces, bem como o [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) e [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) métodos.  
  
 Avaliação de expressão assíncrona exige que você implemente o [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interface e sua [IDebugExpressionEvaluationCompleteEvent2::GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md) [e GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) métodos.  
  
 Eventos síncronos precisam implementar o [IDebugEngine2::ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) método.  
  
 Para o mecanismo gravar a saída de cadeia de caracteres de estilo, você deve implementar o [IDebugOutputStringEvent2::GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [Controle de execução e avaliação de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)