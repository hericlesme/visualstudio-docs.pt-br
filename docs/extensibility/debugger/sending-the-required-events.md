---
title: Enviar os eventos necessários | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: deeffb814dacc58b1fb3a3f993203139d9b1a081
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="sending-the-required-events"></a>Enviar os eventos necessários
Use este procedimento para enviar eventos necessários.  
  
## <a name="process-for-sending-required-events"></a>Processo de envio de eventos necessários  
 Os eventos a seguir são necessários, em ordem, quando criar uma depuração mecanismo (DE) e anexá-lo a um programa:  
  
1.  Enviar um [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) o objeto de evento para o Gerenciador de sessão de depuração (SDM) quando o DE é inicializado para um ou mais programas em um processo de depuração.  
  
2.  Quando o programa a ser depurado está conectado, enviar um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) o objeto de evento para o SDM. Esse evento pode ser um evento de parada, dependendo de seu design de mecanismo.  
  
3.  Se o programa está anexado para quando o processo é iniciado, envie um [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) o objeto de evento para o SDM para notificar o IDE do novo thread. Esse evento pode ser um evento de parada, dependendo de seu design de mecanismo.  
  
4.  Enviar um [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) o objeto de evento para o SDM quando o programa que está sendo depurado é terminado de carregar ou quando anexar ao programa for concluído. Esse evento deve ser um evento de parada.  
  
5.  Se o aplicativo a ser depurado é iniciado, envie um [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) o objeto de evento para o SDM quando a primeira instrução do código na arquitetura de tempo de execução está prestes a ser executada. Esse evento é sempre um evento de parada. Quando entrar na sessão de depuração, o IDE para esse evento.  
  
> [!NOTE]
>  Muitos idiomas usam inicializadores global ou funções externas pré-compilado (da biblioteca CRT ou Main) no início do seu código. Se o idioma do programa que você está depurando contém qualquer um desses tipos de elementos antes do ponto de entrada inicial, em seguida, esse código é executado e o evento de ponto de entrada é enviado quando a usuário ponto de entrada, como **principal** ou `WinMain`, foi atingido.  
  
## <a name="see-also"></a>Consulte também  
 [Habilitar um programa para depuração](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)