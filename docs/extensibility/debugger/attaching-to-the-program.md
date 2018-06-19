---
title: Anexando ao programa | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 9a3f5b83-60b5-4ef0-91fe-a432105bd066
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0a4c9719f6258f3bbb5cc8323693001c7f1a9d47
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107862"
---
# <a name="attaching-to-the-program"></a>Anexando ao programa
Depois de registrar os programas com a porta apropriada, você deve anexar o depurador para o programa que você deseja depurar.  
  
## <a name="choosing-how-to-attach"></a>Escolher como anexar  
 Há três maneiras em que o Gerenciador de sessão de depuração (SDM) tenta anexar o programa que está sendo depurado.  
  
1.  Para programas que são iniciados pelo mecanismo de depuração por meio de [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) método (típico de idiomas interpretados, por exemplo), o SDM obtém o [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) de interface de o [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) objeto associado com o programa que está sendo anexado ao. Se o SDM pode obter o `IDebugProgramNodeAttach2` interface, o SDM, em seguida, chama o [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método. O `IDebugProgramNodeAttach2::OnAttach` método retorna `S_OK` para indicar que não anexada ao programa e que podem ser feitas outras tentativas para anexar ao programa.  
  
2.  Se o SDM pode obter o [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md) de interface do programa que está sendo anexado para as chamadas SDM o [Attach](../../extensibility/debugger/reference/idebugprogramex2-attach.md) método. Essa abordagem é típica para programas que foram iniciados remotamente pelo fornecedor de porta.  
  
3.  Se o programa não pode ser conectado por meio de `IDebugProgramNodeAttach2::OnAttach` ou `IDebugProgramEx2::Attach` métodos, o SDM carrega o mecanismo de depuração (se ainda não estiver carregado) chamando o `CoCreateInstance` função e, em seguida, chama o [anexar](../../extensibility/debugger/reference/idebugengine2-attach.md) método. Essa abordagem é típica para programas localmente iniciados por um fornecedor de porta.  
  
     Também é possível para um fornecedor de porta personalizada chamar o `IDebugEngine2::Attach` método na implementação do fornecedor de porta personalizada do `IDebugProgramEx2::Attach` método. Normalmente nesse caso, o fornecedor de porta personalizada inicia o mecanismo de depuração no computador remoto.  
  
 Anexo é obtido quando o Gerenciador de sessão de depuração (SDM) chama o [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) método.  
  
 Se você executar o DE no mesmo processo que o aplicativo a ser depurado, você deve implementar os seguintes métodos de [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md):  
  
-   [GetHostName](../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md),  
  
-   [GetHostPid](../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)  
  
-   [GetProgramName](../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)  
  
 Após o `IDebugEngine2::Attach` método é chamado, siga estas etapas na implementação do `IDebugEngine2::Attach` método:  
  
1.  Enviar um [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) o objeto de evento para o SDM. Para obter mais informações, consulte [enviar eventos](../../extensibility/debugger/sending-events.md).  
  
2.  Chamar o [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) método o [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) objeto passado para o `IDebugEngine2::Attach` método.  
  
     Isso retorna um `GUID` que é usado para identificar o programa. O `GUID` devem ser armazenados no objeto que representa o local do programa para o DE, e ele deve ser retornado quando o `IDebugProgram2::GetProgramId` método é chamado no `IDebugProgram2` interface.  
  
    > [!NOTE]
    >  Se você implementar o `IDebugProgramNodeAttach2` interface, o programa `GUID` é passado para o `IDebugProgramNodeAttach2::OnAttach` método. Isso `GUID` é usada para o programa `GUID` retornado pelo `IDebugProgram2::GetProgramId` método.  
  
3.  Enviar um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) o objeto de evento para notificar o SDM que local `IDebugProgram2` objeto foi criado para representar o programa DE. Para obter detalhes, consulte [enviar eventos](../../extensibility/debugger/sending-events.md).  
  
    > [!NOTE]
    >  Isso não é o mesmo `IDebugProgram2` objeto que foi passado para o `IDebugEngine2::Attach` método. Anteriormente passado `IDebugProgram2` objeto é reconhecido pelo somente a porta e é um objeto separado.  
  
## <a name="see-also"></a>Consulte também  
 [Anexo de lançamento](../../extensibility/debugger/launch-based-attachment.md)   
 [Envio de eventos](../../extensibility/debugger/sending-events.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Anexar](../../extensibility/debugger/reference/idebugprogramex2-attach.md)   
 [Anexar](../../extensibility/debugger/reference/idebugengine2-attach.md)