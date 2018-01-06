---
title: "Iniciar uma sessão de depuração para um aplicativo UWP no Visual Studio (VB, c#, C++ e XAML) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.IVCAppHostRemoteDebugPageObject.MachineName
- VC.Project.IVCAppHostRemoteDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostLocalDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostTetheredDebugPageObject.DebuggerType
- VC.Project.IVCAppHostLocalDebugPageObject.BreakpointBehavior
- VC.Project.IVCAppHostRemoteDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostRemoteDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.DebuggerType
- ImmersiveProjects.Properties.Debug
- VC.Project.IVCAppHostTetheredDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostSimulatorDebugPageObject.GPUDebuggerTargetType
- VC.Project.IVCAppHostLocalDebugPageObject.LaunchApplication
- VC.Project.IVCAppHostLocalDebugPageObject.AllowLocalNetworkLoopback
- AppPackage.Properties.Debug
- VC.Project.IVCAppHostRemoteDebugPageObject.Authentication
- VC.Project.IVCAppHostRemoteDebugPageObject.DebuggerType
- VC.Project.IVCAppHostSimulatorDebugPageObject.BreakpointBehavior
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 66ec0e79-8261-4c19-a618-3fd1b3f71bbd
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: d99458d8afd6d4789d7827404f38d6dcfea76012
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="start-a-debugging-session-for-a-uwp-app-in-visual-studio-vb-c-c-and-xaml"></a>Iniciar uma sessão de depuração para um aplicativo UWP no Visual Studio (VB, c#, C++ e XAML)
![Aplica-se a Windows e Windows Phone](../debugger/media/windows_and_phone_content.png "windows_and_phone_content")  
  
 Este tópico descreve como iniciar uma sessão de depuração para aplicativos UWP escritos em XAML e Visual C++, Visual c# ou Visual Basic. Depurar um aplicativo envolve configurar a sessão de depuração e escolher a maneira de iniciar o aplicativo.  
  
> [!NOTE]
>  Para aplicativos escritos em JavaScript e HTML, consulte [iniciar uma sessão de depuração (JavaScript)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md).  
  
##  <a name="BKMK_In_this_topic"></a> Neste tópico  
 [A maneira fácil de iniciar a depuração](#BKMK_The_easy_way_to_start_debugging)  
  
 [Configurar a sessão de depuração](#BKMK_Configure_the_debugging_session)  
  
-   [Abra a página de propriedades de depuração para o projeto](#BKMK_Open_the_debugging_property_page_for_the_project)  
  
-   [Escolher opções de configuração de compilação](#BKMK_Choose_the_build_configuration_options)  
  
-   [Escolha o destino de implantação](#BKMK_Choose_the_deployment_target)  
  
-   [Escolher o depurador a ser usado](#BKMK_Choose_the_debugger_to_use)  
  
-   [(Opcional) Atrasar o início da sessão de depuração](#BKMK__Optional__Delay_starting_the_debug_session)  
  
-   [(Opcional) Desabilitar loopbacks de rede](#BKMK__Optional__Disable_network_loopbacks)  
  
-   [(Opcional) Reinstale o aplicativo ao iniciar a depuração](#BKMK__Optional__Reinstall_the_app_when_you_start_debugging)  
  
-   [(Opcional) Desativar a requisição de autenticação para iniciar o depurador remoto](#BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger)  
  
 [Iniciar a sessão de depuração](#BKMK_Start_the_debugging_session)  
  
-   [Iniciar a depuração (F5)](#BKMK_Start_debugging__F5_)  
  
-   [Iniciar a depuração (F5), mas atrasar o início do aplicativo](#BKMK_Start_debugging__F5__but_delay_the_app_start)  
  
-   [Iniciar um aplicativo instalado no depurador](#BKMK_Start_an_installed_app_in_the_debugger)  
  
-   [Anexar o depurador a um aplicativo em execução](#BKMK_Attach_the_debugger_to_a_running_app_)  
  
    -   [Definir o aplicativo para ser executado no modo de depuração](#BKMK_Set_the_app_to_run_in_debug_mode)  
  
    -   [Anexar o depurador](#BKMK_Attach_the_debugger)  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a>A maneira fácil de iniciar a depuração  
  
1.  Abra a solução do aplicativo no Visual Studio.  
  
2.  Escolha F5.  
  
 O Visual Studio compila e inicia o aplicativo com o depurador anexado. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao fim. Para obter mais informações, consulte [navegar por uma sessão de depuração (Xaml e c#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md) .  
  
##  <a name="BKMK_Configure_the_debugging_session"></a>Configurar a sessão de depuração  
  
###  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Abra a página de propriedades de depuração para o projeto  
  
1.  No Gerenciador de Soluções, selecione o projeto. No menu de atalho, escolha **propriedades**.  
  
2.  Faça isso para abrir a página de propriedades de depuração do projeto:  
  
    -   Para aplicativos Visual c# e Visual Basic, escolha **depurar**.  
  
         ![C &#35; &#47; Página de propriedades de depuração de projeto VB](../debugger/media/dbg_csvb_debugpropertypage.png "DBG_CsVb_DebugPropertyPage")  
  
    -   Para aplicativos Visual C++, expanda o **propriedades de configuração** nó e, em seguida, escolha **depuração**.  
  
         ![C &#43; &#43; Página de propriedades de depuração de aplicativo UWP](../debugger/media/dbg_cpp_debugpropertypage.png "DBG_CPP_DebugPropertyPage")  
  
###  <a name="BKMK_Choose_the_build_configuration_options"></a>Escolher opções de configuração de compilação  
  
1.  Do **configuração** , escolha **depurar** ou **(ativo) depurar**.  
  
2.  Do **plataforma** lista escolha a plataforma de destino do build. Na maioria dos casos, **qualquer CPU** (**todas as plataformas** no Visual C++) é a melhor opção.  
  
###  <a name="BKMK_Choose_the_deployment_target"></a>Escolha o destino de implantação  
 ![Aplica-se apenas ao Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 Você pode implantar e depurar um aplicativo UWP no computador com Visual Studio, no simulador do Visual Studio no computador local ou em um dispositivo remoto.  
  
-   Para aplicativos c# e Visual Basic, escolha o destino do **dispositivo de destino** lista o **depurar** página de propriedades do projeto.  
  
-   Para aplicativos em C++, escolha o destino do **depurador a iniciar** lista o **depuração** página de propriedades:  
  
 Escolha uma destas opções:  
  
|||  
|-|-|  
|**Computador local**|Depura o aplicativo na sessão atual no computador local. Consulte [UWP executar aplicativos no computador local](../debugger/run-windows-store-apps-on-the-local-machine.md).|  
|**Simulador**|Depura o aplicativo no simulador do Visual Studio para aplicativos [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]. O simulador é uma janela da área de trabalho que permite depurar recursos, como gestos de toque e rotação de dispositivos, que não estão disponíveis no computador local. Consulte [UWP executar aplicativos no simulador](../debugger/run-windows-store-apps-in-the-simulator.md).|  
|**Computador remoto**|Depura o aplicativo em um dispositivo conectado ao computador local por uma intranet ou diretamente por meio de um cabo Ethernet. Para depurar remotamente, as Ferramentas Remotas do Visual Studio devem estar instaladas e em execução no dispositivo remoto. Consulte [UWP executar aplicativos em um computador remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
  
 Se você escolher **máquina remota**, especifique o nome ou endereço IP do computador remoto em uma das seguintes maneiras:  
  
-   Digite o nome ou endereço IP do computador remoto.  
  
    -   Para aplicativos c# e Visual Basic, digite o nome ou endereço IP do **máquina remota** caixa.  
  
    -   Para aplicativos em C++, digite o nome ou endereço IP no **nome da máquina** caixa.  
  
-   Escolha o computador remoto no **Selecionar Conexão de depurador remoto** caixa de diálogo.  
  
     Para abrir a caixa de diálogo:  
  
    -   Para aplicativos c# e Visual Basic, escolha **localizar**.  
  
    -   Para aplicativos em C++, escolha a seta para baixo no **nome da máquina** caixa e escolha  **\<localizar... >**.  
  
     ![Marque a caixa de diálogo Conexão de depurador remoto](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")  
  
    > [!NOTE]
    >  O **Selecionar Conexão de depurador remoto** caixa de diálogo exibe computadores que estão na sub-rede local e os computadores que estão diretamente conectados ao computador com o Visual Studio por um cabo Ethernet. Para especificar outro computador, digite o nome no **nome da máquina** caixa.  
  
 ![Aplica-se apenas ao Windows Phone](../debugger/media/phone_only_content.png "phone_only_content")  
  
 Você pode implantar e depurar um aplicativo do Windows Phone, em um dispositivo ou em um dos emuladores de telefone do Visual Studio. Selecione o dispositivo ou emulador do **dispositivo de destino** lista.  
  
###  <a name="BKMK_Choose_the_debugger_to_use"></a>Escolher o depurador a ser usado  
 Por padrão, o Visual Studio depura o código gerenciado nos aplicativos em C# e Visual Basic.  
  
 Para aplicativos em C# e Visual Basic, você pode optar por depurar o código gerenciado e o código C/C++ nativo. Selecione o **habilitar a depuração de código não gerenciado** caixa de seleção para incluir o código nativo na sessão de depuração.  
  
 Por padrão, o Visual Studio depura o código nativo no aplicativo em C++.  
  
 Para aplicativos em C++, você pode escolher depurar tipos específicos de código que estão em componentes do seu aplicativo em vez do código nativo ou além dele. Especifique o código para depurar o **tipo de depurador** lista o **depuração** página de propriedades do projeto de aplicativo.  
  
 Escolha um destes depuradores das **processo de aplicativo** lista:  
  
|||  
|-|-|  
|**Somente script**|Depura o código JavaScript no aplicativo. O código gerenciado e o código nativo são ignorados.|  
|**Somente nativo**|Depura o código C/C++ nativo no aplicativo. O código gerenciado e o código JavaScript são ignorados.|  
|**Somente gerenciado**|Depura o código gerenciado no aplicativo. O código JavaScript e o código C/C++ nativo são ignorados.|  
|**Misto (gerenciado e nativo)**|Depura o código C/C++ nativo e o código gerenciado no aplicativo. O código JavaScript é ignorado.|  
|**Somente GPU**|Depurar o código C++ nativo que é executado em uma GPU (unidade de processamento gráfico).|  
  
 ![Aplica-se apenas ao Windows Phone](../debugger/media/phone_only_content.png "phone_only_content")  
  
 Para aplicativos do Windows Phone, você também pode escolher o depurador a ser usado para os processos em segundo plano do **processo de tarefa em segundo plano**.  
  
###  <a name="BKMK__Optional__Delay_starting_the_debug_session"></a>(Opcional) Atrasar o início da sessão de depuração  
 Por padrão, o Visual Studio inicia o aplicativo imediatamente quando você começa a depuração. Você também pode iniciar uma sessão de depuração, mas atrasar o início do seu aplicativo. Quando você escolhe essa opção, o aplicativo é iniciado no depurador quando é executado na tela inicial ou por um contrato de ativação ou quando é iniciado por outro processo ou método. Você também atrasa o início do aplicativo quando deseja depurar uma tarefa em segundo plano quando o aplicativo em si não está em execução.  
  
 Para atrasar a inicialização do aplicativo, você pode fazer o seguinte:  
  
-   Para aplicativos Visual c# e Visual Basic, selecione **não iniciar, mas depurar meu código quando iniciar** no **depurar** página de propriedades.  
  
-   Para aplicativos Visual C++, escolha **Sim** do **Iniciar aplicativo** lista o **depuração** página de propriedades.  
  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a>(Opcional) Desabilitar loopbacks de rede  
 ![Aplica-se apenas ao Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 Por motivos de segurança, um aplicativo UWP instalado da maneira padrão não é permitido para fazer chamadas de rede para o dispositivo que está instalado. Por padrão, a implantação do Visual Studio cria uma isenção dessa regra para o aplicativo implantado. Essa isenção permite que você teste procedimentos de comunicação em um único computador. Antes de enviar seu aplicativo para Microsoft Store, você deve testar seu aplicativo sem a isenção.  
  
 Para remover a isenção de loopback de rede:  
  
-   Para aplicativos Visual c# e Visual Basic, desmarque o **permitir Loopback de rede** caixa de seleção de **depurar** página de propriedades.  
  
-   Para aplicativos Visual C++, escolha **não** do **permitir Loopback de rede** lista o **depuração** página de propriedades.  
  
###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a>(Opcional) Reinstale o aplicativo ao iniciar a depuração  
 Para diagnosticar problemas com a instalação e configuração inicial do seu aplicativo do Visual c# ou Visual Basic, escolha **desinstalar e reinstalar meu pacote** no **depurar** página de propriedades para recriar um instalação original ao iniciar a depuração. Essa opção não está disponível para projetos do Visual C++.  
  
###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a>(Opcional) Desativar a requisição de autenticação para iniciar o depurador remoto  
 ![Aplica-se apenas ao Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 Por padrão, você deve fornecer credenciais para executar o depurador remoto.  
  
> [!IMPORTANT]
>  Você também pode optar por executar o depurador remoto no Modo Sem Autenticação, mas isso é altamente desaconselhável. Nesse modo não há nenhuma segurança de rede. Escolha o Modo Sem Autenticação somente se você tiver certeza de que a rede não corre risco de tráfego mal-intencionado ou hostil.  
  
 Para remover a requisição de autenticação:  
  
1.  Para aplicativos Visual c# e Visual Basic, desmarque o **usar autenticação** caixa de seleção de **depurar** página de propriedades.  
  
2.  Para aplicativos Visual C++, escolha **não** do **requer autenticação** lista o **depuração** página de propriedades.  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Start_the_debugging_session"></a>Iniciar a sessão de depuração  
  
###  <a name="BKMK_Start_debugging__F5_"></a>Iniciar a depuração (F5)  
 Quando você escolhe **iniciar depuração** (teclado: F5) sobre o **depurar** menu, o Visual Studio inicia o aplicativo com o depurador anexado. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção ou o aplicativo chegue ao fim.  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Iniciar a depuração (F5), mas atrasar o início do aplicativo  
 Você pode definir que o aplicativo seja executado no modo de depuração, mas inicie-o por outro método que não seja o depurador. Por exemplo, convém depurar a inicialização do aplicativo no menu Iniciar ou depurar um processo em segundo plano do aplicativo sem iniciá-lo. Para atrasar o início do aplicativo, faça o seguinte:  
  
-   Sobre o **depuração** página de propriedades do aplicativo (**depurar** no Visual C++)  
  
    -   Para aplicativos Visual c# e Visual Basic, escolha **não iniciar, mas depurar meu código quando iniciar**.  
  
    -   Para aplicativos Visual C++, escolha **Sim** do **Iniciar aplicativo** lista.  
  
-   Escolha **iniciar depuração** no **depurar** menu (teclado: F5).  
  
-   Inicie o aplicativo pelo menu Iniciar, por um contrato de execução ou por outro procedimento.  
  
 O aplicativo é iniciado no modo de depuração. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao fim.  
  
 . Para obter mais informações sobre como depurar tarefas em segundo plano, consulte [gatilho suspender, continuar e eventos para aplicativos UWP em segundo plano)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Iniciar um aplicativo instalado no depurador  
 Quando você inicia a depuração usando F5, o Visual Studio compila e implanta o aplicativo, define que ele seja executado no modo de depuração e, em seguida, inicia-o. Para iniciar um aplicativo que já está instalado em um dispositivo, use a caixa de diálogo Depurar Pacote do Aplicativo Instalado. Esse procedimento é útil quando você precisa depurar um aplicativo instalado da Windows Store ou quando você tem os arquivos de origem do aplicativo, mas não tem um projeto do Visual Studio para o aplicativo. Por exemplo, você pode ter um sistema de build personalizado que não use projetos ou soluções do Visual Studio.  
  
 O aplicativo pode ser instalado no dispositivo local ou pode estar localizado em um dispositivo remoto.  É possível iniciar o aplicativo imediatamente ou defini-lo para ser executado no depurador quando for iniciado por outro processo ou método, por exemplo, no menu Iniciar ou por um contrato de ativação. Você também pode definir o aplicativo para ser executado no modo de depuração quando quiser depurar um processo em segundo plano sem iniciar o aplicativo. Para obter mais informações, consulte [gatilho suspender, continuar e eventos para aplicativos UWP em segundo plano)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
 Para definir um aplicativo instalado para ser executado no modo de depuração, faça o seguinte:  
  
> [!NOTE]
>  O aplicativo não deve estar em execução quando você iniciar este procedimento.  
  
1.  Sobre o **depurar** menu, escolha **depurar pacote do aplicativo instalado**  
  
2.  Escolha uma destas opções na lista:  
  
    |||  
    |-|-|  
    |**Computador local**|Depura o aplicativo na sessão atual no computador local. Consulte [UWP executar aplicativos no computador local](../debugger/run-windows-store-apps-on-the-local-machine.md).|  
    |**Simulador**|Depura o aplicativo no simulador do Visual Studio para aplicativos [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]. O simulador é uma janela da área de trabalho que permite depurar recursos, como gestos de toque e rotação de dispositivos, que não estão disponíveis no computador local. Consulte [UWP executar aplicativos no simulador](../debugger/run-windows-store-apps-in-the-simulator.md).|  
    |**Computador remoto**|Depura o aplicativo em um dispositivo conectado ao computador local por uma intranet ou diretamente por meio de um cabo Ethernet. Para depurar remotamente, as Ferramentas Remotas do Visual Studio devem estar instaladas e em execução no dispositivo remoto. Consulte [UWP executar aplicativos em um computador remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
  
3.  Escolha o aplicativo a partir de **instalado pacotes de aplicativos** lista.  
  
4.  Escolha o mecanismo de depuração para usar a partir de **depurar este tipo de código** lista.  
  
5.  (Opcional). Escolha **não iniciar, mas depurar meu código quando iniciar** para depurar o aplicativo quando ele for iniciado por algum outro método ou para depurar um processo em segundo plano.  
  
 Quando você clica em **iniciar**, o aplicativo é iniciado ou definido para ser executado no modo de depuração.  
  
###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Anexar o depurador a um aplicativo em execução  
 Para anexar o depurador a um aplicativo [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)], você deve usar o Gerenciador de Pacotes Depuráveis para definir a execução do aplicativo no modo de depuração. Esse recurso é instalado com as Ferramentas Remotas do Visual Studio.  
  
 Anexar o depurador a um aplicativo é útil quando você precisa depurar um aplicativo já instalado; por exemplo, um que tenha sido instalado da [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]. A anexação é necessária quando você tem os arquivos de origem do aplicativo, mas não tem um projeto do Visual Studio para ele. Por exemplo, você pode ter um sistema de build personalizado que não use projetos ou soluções do Visual Studio.  
  
 Para anexar o depurador a um aplicativo, são necessárias as seguintes etapas:  
  
1.  Defina o aplicativo para ser executado no modo de depuração. Isso deve ser feito quando o aplicativo não está em execução.  
  
2.  Inicie o aplicativo. Você pode fazer isso pela tela inicial, por um contrato de execução ou por outro método.  
  
3.  Anexe o depurador ao aplicativo em execução.  
  
####  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Definir o aplicativo para ser executado no modo de depuração  
  
1.  Instale as Ferramentas Remotas do Visual Studio no dispositivo em que o aplicativo está instalado. Consulte [instalando as ferramentas remotas](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).  
  
2.  Na tela inicial, procure por `Debuggable Package Manager` e inicie-o.  
  
     É exibida uma janela do PowerShell corretamente configurada para o cmdlet AppxDebug.  
  
3.  Para habilitar a depuração de um aplicativo, é preciso especificar o identificador NomeCompletodoPacote do aplicativo. Para ver uma lista de todos os aplicativos que incluem o NomeCompletodoPacote, digite `Get-AppxPackage` no aviso do PowerShell.  
  
4.  No prompt do PowerShell, digite `Enable-AppxDebug` *PackageFullName* onde *PackageFullName* é o identificador PackageFullName do aplicativo.  
  
####  <a name="BKMK_Attach_the_debugger"></a>Anexar o depurador  
 Para anexar o depurador:  
  
1.  Sobre o **depurar** menu, escolha **anexar ao processo**.  
  
     O **anexar ao processo** caixa de diálogo é exibida.  
  
2.  Para anexar a um aplicativo em um dispositivo remoto, especifique o dispositivo remoto no **qualificador** caixa. Você pode:  
  
    -   Digite o nome no **qualificador** caixa.  
  
    -   Escolha a seta para baixo no **qualificador** caixa e, em seguida, escolha o dispositivo em uma lista de dispositivos que você já anexou antes.  
  
    -   Escolha **localizar** para selecionar o dispositivo em uma lista de dispositivos em sua sub-rede local.  
  
3.  Especifique o tipo de código que você deseja depurar no **anexar a** caixa.  
  
     Escolha **selecione** e, em seguida, faça o seguinte:  
  
    -   Escolha **determinar automaticamente o tipo de código a ser depurado**  
  
    -   Escolha **depurar esses tipos de código** e, em seguida, escolha um ou mais tipos na lista.  
  
4.  No **processos disponíveis** , escolha o processo do aplicativo.  
  
5.  Escolha **anexar**.  
  
 O Visual Studio anexa o depurador ao processo. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao fim.  
  
 [Neste tópico](#BKMK_In_this_topic)  
  
## <a name="see-also"></a>Consulte também  
 [Depurar aplicativos no Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   
 [Navegar por uma sessão de depuração (Xaml e c#)](../debugger/navigate-a-debugging-session-in-visual-studio-xaml-and-csharp.md)