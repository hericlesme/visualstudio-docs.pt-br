---
title: Controle de execução | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c9fc47a0b73d07e4b24ef55c736ad80197f282cb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="control-of-execution"></a>Controle de execução
O mecanismo de depuração (DE) normalmente envia um dos eventos a seguir como o último evento de inicialização:  
  
-   O evento de ponto de entrada, se anexar a um programa acabou de ser iniciado  
  
-   O evento de carga completo, se anexar a um programa que já está em execução  
  
 Ambos esses eventos são interrompendo eventos, que significa que o DE espera por uma resposta do usuário por meio do IDE. Para obter mais informações, consulte [modos operacionais](../../extensibility/debugger/operational-modes.md).  
  
## <a name="stopping-event"></a>Interrompendo o evento  
 Quando um evento de parada é enviado para a sessão de depuração:  
  
1.  O programa e o thread que contêm o ponteiro de instrução atual podem ser obtidos na interface do evento.  
  
2.  O IDE determina o atual arquivo de código fonte e a posição, que exibe realçada no editor.  
  
3.  A sessão de depuração normalmente responde a este evento de interrupção primeiro chamando o programa **continuar** método.  
  
4.  O programa é executado, em seguida, até encontrar uma condição de interrupção, como alcançar um ponto de interrupção, no qual o caso DE envia um evento de ponto de interrupção para a sessão de depuração. O ponto de interrupção é um evento de interrupção e o DE novamente aguarda uma resposta do usuário.  
  
5.  Se o usuário opta por intervir, acima ou fora de uma função, o IDE solicita que a sessão de depuração para chamar o programa `Step` método, passando a unidade da etapa (instrução, a instrução ou linha) e o tipo de etapa — ou seja, se entrar em, em , ou sairá da função. Quando a etapa for concluída, o DE envia um evento de conclusão de etapa para a sessão de depuração, que é um evento de parada.  
  
     -ou-  
  
     Se o usuário optar por continuar a executar a partir do ponteiro de instrução atual, o IDE solicita que a sessão de depuração para chamar o programa **Execute** método. O programa continua a execução até que ele encontra a próxima condição de interrupção.  
  
     -ou-  
  
     Se a sessão de depuração é ignorar um evento de interrupção específico, a sessão de depuração chama o programa **continuar** método. Se o programa foi passo a passo em, acima ou fora de uma função quando ela encontrada a condição de interrupção, ele continua a etapa.  
  
 Programaticamente, quando o DE encontra uma condição de interrupção, ele envia eventos parando como [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ou [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) para o Gerenciador de depuração de sessão (SDM) por meio do um [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) interface. Os passos da [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) e [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfaces que representam o programa e o thread que contém o ponteiro de instrução atual. As chamadas SDM [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) para obter o quadro superior da pilha de chamadas [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) para obter o contexto de documento associado à instrução atual ponteiro. Este contexto de documento normalmente é um número de coluna, linha e nome de arquivo do código fonte. O IDE usa para realçar o código-fonte que contém o ponteiro de instrução atual.  
  
 O SDM normalmente responde a este evento de interrupção primeiro chamando [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). O programa é executado, em seguida, até encontrar uma condição de interrupção, como alcançar um ponto de interrupção, no qual o caso DE envia um [IDebugBreakpointEvent2 Interface](../../extensibility/debugger/reference/idebugbreakpointevent2.md) para o SDM. O ponto de interrupção é um evento de interrupção e o DE novamente aguarda uma resposta do usuário.  
  
 Se o usuário opta por intervir, acima ou fora de uma função, o IDE solicita SDM chamar [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md), passando o [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (instrução, a instrução ou linha) e o [ STEPKIND](../../extensibility/debugger/reference/stepkind.md), ou seja, se a etapa em, acima ou sairá da função. Quando a etapa for concluída, o DE envia um [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interface SDM, que é um evento de parada.  
  
 Se o usuário optar por continuar a executar a partir do ponteiro de instrução atual, o IDE solicita SDM chamar [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). O programa continua a execução até que ele encontra a próxima condição de interrupção.  
  
 Se o pacote de depuração é ignorar um evento de interrupção específico, o pacote de depuração chama SDM, que chama [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Se o programa foi passo a passo em, acima ou fora de uma função quando ela encontrada a condição de interrupção, ele continua a etapa. Isso implica que o programa mantém um estado de revisão, para que ele saiba como continuar.  
  
 As chamadas que faz o SDM `Step`, **Execute**, e **continuar** são assíncrona, o que significa que o SDM espera que a chamada para retornar rapidamente. Se o DE envia o SDM um evento de parada no mesmo thread antes de `Step`, **Execute**, ou **continuar** retorna, o SDM trava.  
  
## <a name="see-also"></a>Consulte também  
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)