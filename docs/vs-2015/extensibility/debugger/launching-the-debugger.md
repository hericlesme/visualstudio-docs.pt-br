---
title: Iniciando o depurador | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f2a427825fdc10811fccc10ddc71438b406ebd5b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462059"
---
# <a name="launching-the-debugger"></a>Iniciando o depurador
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [iniciando o depurador](https://docs.microsoft.com/visualstudio/extensibility/debugger/launching-the-debugger).  
  
Iniciando o depurador requer o envio de sequência correta de métodos e eventos com seus atributos apropriados.  
  
## <a name="sequences-of-methods-and-events"></a>Sequências de métodos e eventos  
  
1.  O Gerenciador de sessão de depuração (SDM) é chamado, escolhendo a **Debug** menu e, em seguida, escolhendo **iniciar**. Ver [inicializando um programa](../../extensibility/debugger/launching-a-program.md) para obter mais informações.  
  
2.  As chamadas SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método.  
  
3.  Com base no modelo de processo (DES) do mecanismo de depuração, o `IDebugProgramNodeAttach2::OnAttach` método retorna um dos métodos a seguir, que determina o que acontece em seguida.  
  
     Se `S_FALSE` for retornado, o mecanismo de depuração (DES) deve ser carregado em andamento com a máquina virtual.  
  
     -ou-  
  
     Se `S_OK` for retornado, o DE deve ser carregado no processo do SDM. O SDM, em seguida, executa as seguintes tarefas:  
  
    1.  Chamadas [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) para obter as informações de mecanismo de.  
  
    2.  Cria conjunta DE.  
  
    3.  Chamadas [anexar](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4.  O envia DE um [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) para o SDM com um `EVENT_SYNC` atributo.  
  
5.  O envia DE um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) para o SDM com um `EVENT_SYNC` atributo.  
  
6.  O envia DE um [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) para o SDM com um `EVENT_SYNC` atributo.  
  
7.  O envia DE um [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) para o SDM com um `EVENT_SYNC` atributo.  
  
8.  O envia DE um [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) para o SDM com um `EVENT_SYNC` atributo.  
  
## <a name="see-also"></a>Consulte também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)   
 [Inicializando um programa](../../extensibility/debugger/launching-a-program.md)

