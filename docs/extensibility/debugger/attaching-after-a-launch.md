---
title: Anexar após uma inicialização | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 69f9f9cde76c5fa66294fd2cdbdc5252169e0183
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="attaching-after-a-launch"></a>Anexar após uma inicialização
Depois que um programa tiver sido iniciado, a sessão de depuração está pronta para anexar o mecanismo de depuração (DE) para tal programa.  
  
## <a name="design-decisions"></a>Decisões de design  
 Como a comunicação é mais fácil em um espaço de endereçamento compartilhado, você deve decidir se faz mais sentido para facilitar a comunicação entre a sessão de depuração e DE ou entre o programa e DE. Escolha entre os seguintes:  
  
-   Se faz mais sentido para facilitar a comunicação entre a sessão de depuração e DE, a sessão de depuração cria conjunta DE e pergunta DE anexar ao programa. Isso deixa a sessão de depuração e DE juntos em um espaço de endereço e o ambiente de tempo de execução e o programa juntos em outro.  
  
-   Se faz mais sentido para facilitar a comunicação entre o DE e o programa, o ambiente de tempo de execução conjunta cria DE. Isso deixa SDM em um espaço de endereço e o DE, o ambiente de tempo de execução e o programa juntos em outro. Isso é típico de que é implementado com um interpretador para executar o script de idiomas.  
  
    > [!NOTE]
    >  Como o DE anexa ao programa é dependente de implementação. Comunicação entre o programa e DE também é dependente de implementação.  
  
## <a name="implementation"></a>Implementação  
 Programaticamente, quando o Gerenciador de sessão de depuração (SDM) primeiro recebe o [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) o objeto que representa o programa a ser iniciado, ele chama o [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) método, passando um [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) objeto, que é posteriormente usado para passar os eventos de depuração para o SDM. O `IDebugProgram2::Attach` , em seguida, chama um método de [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método. Para obter mais informações sobre como o SDM recebe o `IDebugProgram2` interface, consulte [notificar a porta](../../extensibility/debugger/notifying-the-port.md).  
  
 Se seu ir precisa ser executado no mesmo espaço de endereço do programa que está sendo depurado, normalmente porque o DE faz parte de um interpretador de execução de um script, o `IDebugProgramNodeAttach2::OnAttach` método retorna `S_FALSE`, indicando que ela foi concluída com o processo de conexão.  
  
 Se, por outro lado, o DE é executado no espaço de endereço do SDM, o `IDebugProgramNodeAttach2::OnAttach` método retorna `S_OK` ou [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interface não é implementada em todos os na [IDebugProgramNode2 ](../../extensibility/debugger/reference/idebugprogramnode2.md) objeto associado com o programa que está sendo depurado. Nesse caso, o [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) método eventualmente é chamado para concluir a operação de anexação.  
  
 No último caso, você deve chamar o [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) método no `IDebugProgram2` objeto passado para o `IDebugEngine2::Attach` método, o repositório o `GUID` no programa de local objeto e, em seguida, retornar esta `GUID` quando o `IDebugProgram2::GetProgramId` método é chamado subsequentemente nesse objeto. O `GUID` é usado para identificar o programa exclusivamente entre os vários componentes de depuração.  
  
 Observe que no caso do `IDebugProgramNodeAttach2::OnAttach` método retornando `S_FALSE`, o `GUID` para usar para o programa é passada para este método e é o `IDebugProgramNodeAttach2::OnAttach` método que define o `GUID` no objeto de programa local.  
  
 O DE agora está anexado ao programa e pronto para enviar os eventos de inicialização.  
  
## <a name="see-also"></a>Consulte também  
 [Anexar diretamente a um programa](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Notificar a porta](../../extensibility/debugger/notifying-the-port.md)   
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Anexar](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Anexar](../../extensibility/debugger/reference/idebugengine2-attach.md)