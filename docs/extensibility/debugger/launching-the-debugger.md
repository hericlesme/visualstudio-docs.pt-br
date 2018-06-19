---
title: Iniciando o depurador | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2606e0f6c7d5dfe17e4c82528c36b3f7cdc26c5e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108924"
---
# <a name="launching-the-debugger"></a>Iniciando o depurador
Iniciando o depurador requer o envio de sequência correta de métodos e eventos com seus atributos apropriados.  
  
## <a name="sequences-of-methods-and-events"></a>Sequências de métodos e eventos  
  
1.  O Gerenciador de sessão de depuração (SDM) é chamado, escolhendo o **depurar** menu e, em seguida, escolhendo **iniciar**. Consulte [iniciar um programa](../../extensibility/debugger/launching-a-program.md) para obter mais informações.  
  
2.  As chamadas SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método.  
  
3.  Com base no modelo de processo do mecanismo (DE) de depuração, o `IDebugProgramNodeAttach2::OnAttach` método retorna um dos métodos a seguir, que determina o que acontece em seguida.  
  
     Se `S_FALSE` for retornado, o mecanismo de depuração (DE) é a ser carregado no processo de máquina virtual.  
  
     -ou-  
  
     Se `S_OK` for retornado, é o DE ser carregado no processo do SDM. O SDM, em seguida, executa as seguintes tarefas:  
  
    1.  Chamadas [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) para obter as informações de mecanismo de.  
  
    2.  Cria conjunta DE.  
  
    3.  Chamadas [anexar](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4.  O envia DE um [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) para SDM com um `EVENT_SYNC` atributo.  
  
5.  O envia DE um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) para SDM com um `EVENT_SYNC` atributo.  
  
6.  O envia DE um [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) para SDM com um `EVENT_SYNC` atributo.  
  
7.  O envia DE um [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) para SDM com um `EVENT_SYNC` atributo.  
  
8.  O envia DE um [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) para SDM com um `EVENT_SYNC` atributo.  
  
## <a name="see-also"></a>Consulte também  
 [Eventos do depurador de chamada](../../extensibility/debugger/calling-debugger-events.md)   
 [Inicializando um programa](../../extensibility/debugger/launching-a-program.md)