---
title: Notificar a porta | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports, notification
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1420ca8768ddf1eaedc0d515810bc88b3491c4db
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="notifying-the-port"></a>Notificar a porta
Depois de iniciar um programa, a porta deve ser notificada, da seguinte maneira:  
  
1.  Quando uma porta recebe um novo nó de programa, ele envia um evento de criação de programa para a sessão de depuração. O evento carrega uma interface que representa o programa.  
  
2.  A sessão de depuração consulta o programa para o identificador de um mecanismo de depuração (DE) que pode se conectar ao.  
  
3.  A sessão de depuração verifica se o DE está na lista de permitidos DEs para o programa. A sessão de depuração obtém essa lista de configurações de programa ativo da solução, originalmente passadas a ele pelo pacote de depuração.  
  
     O DE deve estar na lista de permitidos ou que a DE não será anexada ao programa.  
  
 Programaticamente, quando uma porta primeiro recebe um novo nó de programa, ele cria um [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interface para representar o programa.  
  
> [!NOTE]
>  Isso não deve ser confundido com o `IDebugProgram2` interface criado posteriormente pelo mecanismo de depuração (DE).  
  
 A porta envia um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) eventos de criação de programa para o Gerenciador de depuração de sessão (SDM) por meio de um COM `IConnectionPoint` interface.  
  
> [!NOTE]
>  Isso não deve ser confundido com o `IDebugProgramCreateEvent2` interface, que é enviada posteriormente por DE.  
  
 Junto com a interface de evento em si, a porta envia o [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md), e [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfaces, que representam a porta, processam, e programa, respectivamente. As chamadas SDM [IDebugProgram2::GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) para obter o GUID do DE que pode depurar o programa. O GUID originalmente foi obtido o [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interface.  
  
 O SDM verifica se o DE está na lista de permitidos DEs. O SDM obtém essa lista de configurações de programa ativo da solução, originalmente passadas a ele pelo pacote de depuração. O DE deve estar na lista de permitidos, caso contrário, não será anexado ao programa.  
  
 Depois que a identidade do DE é conhecida, o SDM está pronto para anexá-lo para o programa.  
  
## <a name="see-also"></a>Consulte também  
 [Iniciando um programa](../../extensibility/debugger/launching-a-program.md)   
 [Anexar após uma inicialização](../../extensibility/debugger/attaching-after-a-launch.md)   
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)