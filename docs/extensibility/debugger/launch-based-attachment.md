---
title: Anexo com base em Iniciar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 892518cc92286f9415e39c96b6ed2afa8eb0d792
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099370"
---
# <a name="launch-based-attachment"></a>Anexo de lançamento
Anexo com base em Iniciar em um programa é automático. Quando o processo que hospeda o programa é iniciado pelo SDM, anexo de inicialização segue um caminho semelhante a que o método de anexo manual. Para obter informações, consulte [anexando ao programa](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>O processo de anexar  
 A principal diferença é a sequência de eventos a seguir o **Attach** chamar, da seguinte maneira:  
  
1.  Enviar um **IDebugEngineCreateEvent2** o objeto de evento para o SDM. Para obter detalhes, consulte [enviar eventos](../../extensibility/debugger/sending-events.md).  
  
2.  Chamar o `IDebugProgram2::GetProgramId` método no **IDebugProgram2** interface passada para o **Attach** método.  
  
3.  Enviar um **IDebugProgramCreateEvent2** o objeto de evento para notificar o SDM que local **IDebugProgram2** objeto foi criado para representar o programa DE.  
  
4.  Enviar um [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) o objeto de evento para notificar o SDM que um novo segmento é criado para o processo iniciado.  
  
## <a name="see-also"></a>Consulte também  
 [Enviar os eventos necessários](../../extensibility/debugger/sending-the-required-events.md)   
 [Habilitar um programa para depuração](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)