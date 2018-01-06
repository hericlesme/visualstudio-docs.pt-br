---
title: "Envio de eventos de inicialização após uma inicialização | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 65e05d7da2acf5bd3eaf8dab1e3781d3d5b244a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sending-startup-events-after-a-launch"></a>Envio de eventos de inicialização após uma inicialização
Depois que o mecanismo de depuração (DE) é anexado ao programa, ele envia uma série de eventos de inicialização para a sessão de depuração.  
  
 Eventos de inicialização enviados de volta para a sessão de depuração incluem o seguinte:  
  
-   Um evento de criação de mecanismo.  
  
-   Um evento de criação do programa.  
  
-   Criação e eventos de módulo de carregamento do thread.  
  
-   Um evento complete carga, enviado quando o código é carregado e pronto para ser executado, mas antes de qualquer código ser executado  
  
    > [!NOTE]
    >  Quando esse evento é continuado, as variáveis globais são inicializadas e executar rotinas de inicialização.  
  
-   Outros possíveis thread criação e eventos de carregamento de módulo.  
  
-   Um evento de ponto de entrada, que indica que o programa atingiu seu ponto de entrada principal, como **principal** ou `WinMain`. Esse evento não é enviado normalmente se anexa o DE um programa que já está em execução.  
  
 O DE programaticamente, primeiro o Gerenciador de sessão de depuração (SDM) envia um [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interface, que representa um evento de criação de mecanismo, seguido por um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , que representa um evento de criação do programa.  
  
 Isso é geralmente seguido por um ou mais [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) eventos de criação de threads e [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) eventos de carregamento de módulo.  
  
 Quando o código é carregado e pronto para ser executado, mas antes de qualquer código é executado, o DE envia o SDM um [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) evento de conclusão de carregamento. Por fim, se o programa não estiver sendo executado, o DE envia um [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) evento de ponto de entrada, sinalizando que o programa atingiu seu ponto de entrada principal e está pronto para depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Controle de execução](../../extensibility/debugger/control-of-execution.md)   
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)