---
title: Iniciando um programa | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 29e05c7cef8b7bc8644ccbf7ea542e2f043547a6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="launching-a-program"></a>Iniciando um programa
Os usuários que desejam depurar um programa podem pressionar F5 para executar o depurador do IDE. Isso inicia uma série de eventos que resultam, por fim, o IDE conectar-se ao mecanismo de depuração (DE), que por sua vez conectado, ou anexado, o programa da seguinte maneira:  
  
1.  Primeiro, o IDE chama o pacote do projeto para obter configurações de depuração de projeto ativo da solução. As configurações incluem o diretório inicial, as variáveis de ambiente, a porta na qual o programa será executado e o DE ser usado para criar o programa, se especificado. Essas configurações são passadas para o pacote de depuração.  
  
2.  Se a DE for especificada, o DE chamadas do sistema operacional para iniciar o programa. Como consequência de iniciar o programa, o ambiente de tempo de execução do programa é carregado. Por exemplo, se um programa está escrito na MSIL, o common language runtime será chamado para executar o programa.  
  
     -ou-  
  
     Se a DE não for especificada, a porta chama o sistema operacional para iniciar o programa, o que faz com que o ambiente de tempo de execução do programa a ser carregado.  
  
    > [!NOTE]
    >  Se um DE é usado para iniciar um programa, é provável que o mesmo DE será anexado ao programa.  
  
3.  Dependendo se a porta ou o DE iniciado o programa, o DE ou o ambiente de tempo de execução, em seguida, cria uma descrição do programa, ou um nó e notifica a porta que o programa está em execução.  
  
    > [!NOTE]
    >  É recomendável que o ambiente de tempo de execução criar nó do programa, como o nó do programa é uma representação leve de um programa que pode ser depurado. Não é necessário para carregar um inteiro DE apenas para criar e registrar um nó de programa. Se o DE foi projetado ser executado no processo do IDE, mas nenhum IDE está realmente em execução, deve haver um componente que pode adicionar um nó de programa para a porta.  
  
 O programa recentemente criado, junto com outros programas, relacionadas ou não relacionados, iniciado ou anexados a partir do mesmo IDE, compor uma sessão de depuração.  
  
 Programaticamente, quando o usuário primeiro pressiona **F5**, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]do pacote de depuração chama o pacote do projeto (que está associado com o tipo de programa que está sendo iniciado) por meio de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> método, que por sua vez preenche um <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> estrutura com configurações de depuração do projeto ativo da solução. Essa estrutura é passada de volta para o pacote de depuração por meio de uma chamada para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> método. O pacote de depuração instancia o Gerenciador de depuração de sessão (SDM), que inicia o programa que está sendo mecanismos de depuração depurado e qualquer associado.  
  
 Um dos argumentos passados para o SDM é o GUID da ser usado para iniciar o programa.  
  
 Se o GUID DE não `GUID_NULL`, o SDM cria conjunta DE e, em seguida, chama seus [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) método para iniciar o programa. Por exemplo, se um programa for escrito em código nativo, em seguida, `IDebugEngineLaunch2::LaunchSuspended` provavelmente chamará `CreateProcess` e `ResumeThread` (Win32 funções) para executar o programa.  
  
 Como consequência de iniciar o programa, o ambiente de tempo de execução do programa é carregado. O DE ou o ambiente de tempo de execução, em seguida, cria um [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) para descrever o programa de interface e passa a esta interface [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) para notificar a porta que o programa em execução.  
  
 Se `GUID_NULL` for passado, a porta inicia o programa. Quando o programa estiver em execução, o ambiente de tempo de execução cria um `IDebugProgramNode2` para descrever o programa de interface e passa-o para `IDebugPortNotify2::AddProgramNode`. Isso notifica a porta que o programa está em execução. Em seguida, o SDM anexa o mecanismo de depuração para o programa em execução.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Notificar a porta](../../extensibility/debugger/notifying-the-port.md)  
 Explica o que acontece depois que um programa é iniciado e a porta é notificada.  
  
 [Anexar após uma inicialização](../../extensibility/debugger/attaching-after-a-launch.md)  
 Documentos quando a sessão de depuração está pronta para anexação DE para o programa.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)  
 Contém links para várias tarefas de depuração, como iniciar um programa e avaliar expressões.