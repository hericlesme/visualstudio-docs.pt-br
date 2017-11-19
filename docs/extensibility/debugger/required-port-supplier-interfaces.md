---
title: "Porta Supplier Interfaces necessárias | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 973d191305383967aee1c7379fd203375a71c825
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="required-port-supplier-interfaces"></a>A porta necessária Supplier Interfaces
Um fornecedor de porta deve implementar o [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interface.[ IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Como um fornecedor de porta fornece portas, ele também deve implementar. Portanto, ele deve implementar as seguintes interfaces:  
  
-   [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Descreve a porta e pode enumerar todos os processos em execução na porta.  
  
-   [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Fornece para iniciar e encerrar processos na porta.  
  
-   [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Fornece um mecanismo para programas em execução no contexto dessa porta para notificá-lo de destruição e criação de nó do programa. Para obter mais informações, consulte [programa nós](../../extensibility/debugger/program-nodes.md).  
  
-   `IConnectionPointContainer`  
  
     Fornece um ponto de conexão para [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## <a name="port-supplier-operation"></a>Operação de fornecedor de porta  
 O [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) coletor recebe notificações quando os processos e programas que são criados e destruídos em uma porta. Uma porta é necessário para enviar [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) quando um processo é criado e [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) quando um processo é destruído na porta. Uma porta também é necessário para enviar [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) quando um programa é criado e [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) quando um programa é destruído em um processo em execução na porta.  
  
 Uma porta normalmente programa envia criar e destruir eventos em resposta ao [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) e [RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) métodos, respectivamente.  
  
 Como uma porta pode iniciar e encerrar processos físicos e lógicos programas, essas interfaces também deverá ser implementadas pelo mecanismo de depuração:  
  
-   [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
     Descreve o processo físico. Pelo menos devem ser implementados os seguintes métodos:  
  
    -   [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  
  
    -   [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  
  
    -   [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
    -   [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  
  
    -   [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  
  
-   [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
     Fornece uma maneira de SDM anexar e desanexar próprio de um processo.  
  
-   [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
     Descreve o programa lógico. Pelo menos devem ser implementados os seguintes métodos:  
  
    -   [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  
  
    -   [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  
  
    -   [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
-   [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     Fornece uma maneira de SDM conectar a este programa.  
  
## <a name="see-also"></a>Consulte também  
 [Implementar um fornecedor de porta](../../extensibility/debugger/implementing-a-port-supplier.md)