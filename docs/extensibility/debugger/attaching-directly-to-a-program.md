---
title: Anexar diretamente a um programa | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6885cb0dea801ab95e2e88e3f8168c139fea0e0c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100371"
---
# <a name="attaching-directly-to-a-program"></a>Anexar diretamente a um programa
Os usuários que desejam depurar programas em um processo que está sendo executado normalmente siga este processo:  
  
1.  No IDE, escolha o **depurar processos** comando o **ferramentas** menu.  
  
     O **processos** caixa de diálogo é exibida.  
  
2.  Escolha um processo e clique no **Attach** botão.  
  
     O **anexar ao processo** caixa de diálogo é exibida, listando todos os mecanismos de depuração (DEs) instalados no computador.  
  
3.  Especifique o DEs usar para depurar o processo selecionado e, em seguida, clique em **Okey**.  
  
 O pacote de depuração inicia uma sessão de depuração e passa a lista de DEs para ele. A sessão de depuração passa essa lista, junto com uma função de retorno de chamada, para o processo selecionado e, em seguida, solicita que o processo para enumerar seus programas em execução.  
  
 Programaticamente, em resposta à solicitação de usuário, o pacote de depuração instancia o Gerenciador de sessão de depuração (SDM) e passa a lista de DEs selecionado a ele. Juntamente com a lista, o pacote de depuração passa o SDM um [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) interface. O pacote de depuração passa a lista de DEs para o processo selecionado chamando [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Em seguida, chama o SDM [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) na porta para enumerar os programas em execução no processo.  
  
 Esse ponto em diante, cada mecanismo de depuração está anexado a um programa exatamente conforme detalhado no [anexando após um inicie](../../extensibility/debugger/attaching-after-a-launch.md), com duas exceções.  
  
 Para eficiência, DEs que são implementados para compartilhar um espaço de endereço com o SDM são agrupados de forma que cada Ir tem um conjunto de programas, ele será anexado ao. Nesse caso, [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) chamadas [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) e passa uma matriz de programas para anexar.  
  
 A segunda exceção é que os eventos de inicialização enviados por um DE anexar a um programa que está sendo executado normalmente não incluem o evento de ponto de entrada.  
  
## <a name="see-also"></a>Consulte também  
 [Envio de eventos de inicialização após uma inicialização](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)