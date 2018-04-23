---
title: Encerrando um programa | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bc5d711783b3238c9cfe42ba3fc4edd776bcb060
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="terminating-a-program"></a>Encerrando um programa
A seguir está uma descrição do encerramento de um único programa com um thread.  
  
## <a name="termination-process"></a>Processo de encerramento  
  
1.  O envia DE um [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) com uma validade [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2.  O envia DE um [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) com uma validade [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
 O IDE entra no modo de design. O mecanismo de depuração ou ambiente de tempo de execução chama [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) para remover o programa da porta.  
  
## <a name="see-also"></a>Consulte também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)