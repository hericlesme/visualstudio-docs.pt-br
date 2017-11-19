---
title: Iniciando o depurador | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 23fd772b74c4caafbde37541933c38e306f9dc75
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
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