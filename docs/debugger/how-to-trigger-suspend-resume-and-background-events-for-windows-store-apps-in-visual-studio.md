---
title: Como disparar suspender, continuar e eventos em segundo plano durante a depuração de aplicativos UWP | Microsoft Docs
ms.custom: ''
ms.date: 01/16/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.background_task_activate_failure
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 510c79a4d225e250d4c832155da15b61c8c5b055
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280006"
---
# <a name="how-to-trigger-suspend-resume-and-background-events-while-debugging-uwp-apps-in-visual-studio"></a>Como disparar suspender, continuar e eventos em segundo plano durante a depuração de aplicativos UWP no Visual Studio
Quando você não está depurando, Windows **gerenciamento de tempo de vida do processo** (PLM) controla o estado de execução do seu aplicativo — iniciando, suspendendo, retomando e encerrando o aplicativo em resposta às ações do usuário e o estado do dispositivo. Quando você está depurando, o Windows desabilita esses eventos de ativação. Este tópico descreve como acionar esses eventos no depurador.  
  
 Este tópico também descreve como depurar **tarefas em segundo plano**. Essas tarefas permitem que você execute certas operações em um processo em segundo plano, mesmo quando o aplicativo não está sendo executado. Você pode usar o depurador para colocar o aplicativo no modo de depuração e depois, sem iniciar a interface de usuário, iniciar e depurar a tarefa em segundo plano.  
  
 Para obter mais informações sobre tarefas de gerenciamento de tempo de vida do processo e em segundo plano, consulte [Iniciar, retomar e multitarefa](/windows/uwp/launch-resume/index).  
  
##  <a name="BKMK_Trigger_Process_Lifecycle_Management_events"></a> Eventos de gerenciamento de tempo de vida do processo de gatilho  
 O Windows pode suspender o aplicativo quando o usuário sai dele ou quando o Windows entra em um estado de baixo consumo de energia. Você pode responder ao evento `Suspending` para salvar dados relevantes do aplicativo e do usuário em um armazenamento persistente e para liberar recursos. Quando um aplicativo é retomado do **Suspended** de estado, ele entra a **executando** de estado e continua de onde estava quando foi suspenso. Você pode responder ao evento `Resuming` para restaurar ou atualizar o estado do aplicativo e recuperar recursos.  
  
 Embora o Windows tente manter o máximo possível de aplicativos suspensos na memória, ele poderá terminar o aplicativo se não houver recursos suficientes para mantê-lo na memória. Um usuário também pode fechar o aplicativo explicitamente. Não há nenhum evento especial para indicar que o usuário fechou um aplicativo.  
  
 No depurador do Visual Studio, você pode manualmente suspender, retomar e terminar seus aplicativos para depurar eventos do ciclo de vida do processo. Para depurar um evento do ciclo de vida do processo:  
  
1.  Defina um ponto de interrupção no manipulador do evento que você deseja depurar.  
  
2.  Pressione **F5** para iniciar a depuração.  
  
3.  Sobre o **local de depuração** barra de ferramentas, escolha o evento que você deseja acionar:  
  
     ![Suspender, retomar, encerrar e tarefas em segundo plano](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")  
  
     Observe que **suspender e encerrar** fecha o aplicativo e encerra a sessão de depuração.  
  
##  <a name="BKMK_Trigger_background_tasks"></a> Tarefas em segundo plano de gatilho  
 Qualquer aplicativo pode registrar uma tarefa em segundo plano para responder a determinados eventos do sistema, mesmo quando o aplicativo não está sendo executado. As tarefas em segundo plano não podem executar o código que atualiza diretamente a interface do usuário; em vez disso, elas mostram informações para o usuário com atualizações de bloco, atualizações de notificação e notificações do sistema. Para obter mais informações, consulte [que dão suporte a seu aplicativo com tarefas em segundo plano](https://msdn.microsoft.com/library/4c7bb148-eb1f-4640-865e-41f627a46e8e)  
  
 Você pode disparar os eventos que iniciam as tarefas em segundo plano do aplicativo por meio do depurador.  
  
> [!NOTE]
>  O depurador só pode disparar os eventos que não contêm dados, como os que indicam uma alteração de estado no dispositivo. Você precisa disparar manualmente as tarefas em segundo plano que exigem a entrada do usuário ou outros dados.  
  
 A maneira mais realística de disparar um evento de tarefa em segundo plano é quando o aplicativo não está sendo executado. No entanto, também é possível disparar o evento em uma sessão de depuração padrão.  
  
###  <a name="BKMK_Trigger_a_background_task_event_from_a_standard_debug_session"></a> Disparar um evento de tarefa do plano de fundo de uma sessão de depuração padrão  
  
1.  Defina um ponto de interrupção no código de tarefa em segundo plano que você deseja depurar.  
  
2.  Pressione **F5** para iniciar a depuração.  
  
3.  Na lista de eventos sobre o **local de depuração** barra de ferramentas, escolha a tarefa em segundo plano que você deseja iniciar.  
  
     ![Suspender, retomar, encerrar e tarefas em segundo plano](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")  
  
###  <a name="BKMK_Trigger_a_background_task_when_the_app_is_not_running"></a> Disparar uma tarefa em segundo plano quando o aplicativo não está em execução  
  
1.  Defina um ponto de interrupção no código de tarefa em segundo plano que você deseja depurar.  
  
2.  Abra a página de propriedades de depuração do projeto de inicialização. No Gerenciador de Soluções, selecione o projeto. Sobre o **Debug** menu, escolha **propriedades**.  
  
     Para projetos C++ e JavaScript, expanda **propriedades de configuração** e, em seguida, escolha **depuração**.  
  
3.  Realize um dos seguintes procedimentos:  
  
    -   Para projetos do Visual c# e Visual Basic, escolha **não iniciar, mas depurar meu código quando ele é iniciado**  
  
         ![C&#35;&#47;propriedade de aplicativo de inicialização de depuração VB](../debugger/media/dbg_csvb_dontlaunchapp.png "DBG_CsVb_DontLaunchApp")  
  
    -   Para projetos em JavaScript e Visual C++, escolha **nenhuma** da **Iniciar aplicativo** lista.  
  
         ![C&#43;&#43;&#47;propriedade de depuração do aplicativo inicie VB](../debugger/media/dbg_cppjs_dontlaunchapp.png "DBG_CppJs_DontLaunchApp")  
  
4.  Pressione **F5** para colocar o aplicativo no modo de depuração. Observe a **processo** lista os **local de depuração** barra de ferramentas exibe o nome do pacote de aplicativo para indicar que você está no modo de depuração.  
  
     ![Lista de processos de tarefa em segundo plano](../debugger/media/dbg_backgroundtask_processlist.png "DBG_BackgroundTask_ProcessList")  
  
5.  Na lista de eventos sobre o **local de depuração** barra de ferramentas, escolha a tarefa em segundo plano que você deseja iniciar.  
  
     ![Suspender, retomar, encerrar e tarefas em segundo plano](../debugger/media/dbg_suspendresumebackground.png "DBG_SuspendResumeBackground")  
  
##  <a name="BKMK_Trigger_Process_Lifetime_Management_events_and_background_tasks_from_an_installed_app"></a> Disparar eventos de gerenciamento de tempo de vida de processos e tarefas de um aplicativo instalado em segundo plano  
 Use o **depurar pacote do aplicativo instalado** caixa de diálogo para carregar um aplicativo que já está instalado no depurador. Por exemplo, você pode depurar um aplicativo que tenha sido instalado na Microsoft Store ou depurar um aplicativo quando você tem os arquivos de origem para o aplicativo, mas não um projeto do Visual Studio para o aplicativo. O **depurar pacote do aplicativo instalado** caixa de diálogo permite que você inicia um aplicativo no modo de depuração na máquina do Visual Studio ou em um dispositivo remoto, ou para definir o aplicativo seja executado no modo de depuração, mas não iniciá-lo. Para obter mais informações, consulte [depurar pacote de aplicativo instalado](../debugger/debug-installed-app-package.md).
  
 Após o aplicativo ser carregado no depurador, você poderá executar qualquer um dos procedimentos acima.  
  
##  <a name="BKMK_Diagnosing_background_task_activation_errors"></a> Diagnosticando erros de ativação de tarefa em segundo plano  
 Os logs de diagnóstico no Visualizador de eventos do Windows para a infraestrutura de plano de fundo contém informações detalhadas que você pode usar para diagnosticar e solucionar problemas de erros de tarefa em segundo plano. Para exibir o log:  
  
1.  Abra o aplicativo visualizador de eventos.  
  
2.  No **ações** painel, escolha **exibição** e verifique se **Mostrar Logs analíticos e depuração** é verificada.  
  
3.  Sobre o **Visualizador de eventos (Local)** de árvore, expanda os nós **Applications and Services Logs** > **Microsoft** > **Windows**   >  **BackgroundTasksInfrastructure**.  
  
4.  Escolha o **diagnóstico** log.  
  
## <a name="see-also"></a>Consulte também  
 [Testando aplicativos UWP com o Visual Studio](../test/testing-store-apps-with-visual-studio.md)   
 [Depurar aplicativos no Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Ciclo de vida do aplicativo](/windows/uwp/launch-resume/app-lifecycle)   
 [Iniciando, retomar e execução multitarefa](/windows/uwp/launch-resume/index)