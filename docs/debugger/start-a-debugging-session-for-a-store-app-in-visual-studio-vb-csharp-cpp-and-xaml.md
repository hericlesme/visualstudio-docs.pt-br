---
title: "Iniciar uma sessão de depuração para um aplicativo UWP no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/04/2018
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
ms.openlocfilehash: 367fc334d0268a73e8ad1a33ebdc6e74036ddc86
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="start-a-debugging-session-for-a-uwp-app-in-visual-studio"></a>Iniciar uma sessão de depuração para um aplicativo UWP no Visual Studio
  
 Este tópico descreve como iniciar uma sessão de depuração para aplicativos UWP escritos em XAML e Visual C++, Visual c# ou Visual Basic e para aplicativos UWP elaborados em HTML e JavaScript. Depurar um aplicativo envolve configurar a sessão de depuração e escolher a maneira de iniciar o aplicativo.  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a>A maneira fácil de iniciar a depuração  
  
1.  Abra a solução do aplicativo no Visual Studio.  
  
2.  Escolha F5.  
  
 O Visual Studio compila e inicia o aplicativo com o depurador anexado. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao fim.  
  
##  <a name="BKMK_Choose_the_build_configuration_options"></a>Escolher opções de configuração de compilação  
  
1.   Na lista suspensa lista ao lado de **iniciar depuração** botão na **padrão** barra de ferramentas, escolha **depurar**.  
  
2.  Do **plataforma** lista escolha a plataforma de destino do build.  
  
##  <a name="BKMK_Choose_the_deployment_target"></a>Escolha o destino de implantação  
  
Você pode implantar e depurar um aplicativo UWP no computador do Visual Studio, um dispositivo conectado, o simulador do Visual Studio no computador local, um dispositivo remoto ou um emulador. Selecione o destino de implantação na lista suspensa à direita do **plataforma** destino do depurador **padrão** barra de ferramentas.
  
![Selecione um destino de implantação](../debugger/media/vsrun_select_target_device.png)  
  
Escolha uma destas opções:  
  
|||  
|-|-|  
|**Computador local**|Depura o aplicativo na sessão atual no computador local.|  
|**Simulador**|Depura o aplicativo no simulador do Visual Studio para UWP e [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplicativos. O simulador é uma janela de área de trabalho que permite depurar recursos, como gestos de toque e rotação de dispositivos — que pode não estar disponível no computador local. Essa opção só estará disponível se seu aplicativo **mínima da plataforma de destino. Versão** é menor ou igual ao sistema operacional no computador de desenvolvimento. Consulte [UWP executar aplicativos no simulador](../debugger/run-windows-store-apps-in-the-simulator.md).|  
|**Computador remoto**|Depura o aplicativo em um dispositivo conectado ao computador local por uma intranet ou diretamente por meio de um cabo Ethernet. Para depurar remotamente, as ferramentas remotas para Visual Studio deve ser instalado e em execução no dispositivo remoto. Consulte [UWP executar aplicativos em um computador remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
|**Dispositivo**|Depura o aplicativo em um dispositivo USB conectado. O dispositivo deve ser o desbloqueio de desenvolvedor e ter a tela desbloqueada.|  
|**Emulador móvel**|Um emulador de inicialização com a configuração especificada no nome do emulador, implantar o aplicativo e iniciar a depuração. Emuladores só estão disponíveis em máquinas do Hyper-V habilitado executando Windows 8.1 ou versões posteriores.|  

##  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Escolha as opções adicionais de depuração  

Se você precisa configurar opções adicionais de depuração, abra a página de propriedades do projeto.
  
1.  No Gerenciador de Soluções, selecione o projeto. No menu de atalho, escolha **propriedades**.  
  
2.  Faça isso para abrir a página de propriedade de depuração para o projeto:  
  
    -   Para aplicativos Visual c# e Visual Basic, escolha **depurar**.  
  
         ![C &#35; &#47; Página de propriedades de depuração de projeto do VB](../debugger/media/dbg_csvb_debugpropertypage.png)  
  
    -   Para aplicativos Visual C++ e JavaScript, expanda o **propriedades de configuração** nó e, em seguida, escolha **depuração**.  
  
         ![C &#43; &#43; Página de propriedades de depuração de aplicativos UWP](../debugger/media/dbg_cpp_debugpropertypage.png)  

###  <a name="BKMK_Choose_the_debugger_to_use"></a>Escolher o depurador a ser usado  
Por padrão, o Visual Studio depura o código gerenciado nos aplicativos em C# e Visual Basic. Para aplicativos em C# e Visual Basic, você pode optar por depurar o código gerenciado e o código C/C++ nativo. Aplicativos em C++, Visual Studio depura o código nativo por padrão. Em aplicativos JavaScript, Visual Studio depura o script por padrão. 
  
Para aplicativos em C++ e JavaScript, você pode escolher depurar tipos específicos de código que estão em componentes do seu aplicativo em vez de ou além dele, o código nativo. Especifique o código para depurar o **tipo de depurador** lista o **depuração** página de propriedades do projeto de aplicativo.  
  
Escolha um destes depuradores das **processo de aplicativo** lista:  
  
|||  
|-|-|  
|**Somente gerenciado**|Depura o código gerenciado no aplicativo. O código JavaScript e o código C/C++ nativo são ignorados.|  
|**Somente nativo**|Depura o código C/C++ nativo no aplicativo. O código gerenciado e o código JavaScript são ignorados.|  
|**Misto (gerenciado e nativo)**|Depura o código C/C++ nativo e o código gerenciado no aplicativo. O código JavaScript é ignorado. Em projetos do C++, essa opção é chamada de **(gerenciado e nativo)**.|  
|**Somente script**|Depura o código JavaScript no aplicativo. O código gerenciado e o código nativo são ignorados.|  
|**Script e nativo**|Depura o código C/C++ nativo e o código JavaScript no aplicativo. Código gerenciado é ignorado. Disponível em projetos do C++ somente.|  
|**Somente GPU (C++ AMP)**|Depurar o código C++ nativo que é executado em uma GPU (unidade de processamento gráfico). Disponível em projetos do C++ somente.|  

Em aplicativos c# e Visual Basic, você também pode definir o mesmo **tipo de depurador** valores para as tarefas em segundo plano que fazem parte do projeto.
  
###  <a name="BKMK__Optional__Delay_starting_the_debug_session"></a>(Opcional) Atrasar o início da sessão de depuração  
 Por padrão, o Visual Studio inicia o aplicativo imediatamente quando você começa a depuração. Você também pode iniciar uma sessão de depuração, mas atrasar o início do seu aplicativo. Quando você escolhe essa opção, o aplicativo é iniciado no depurador quando é executado na tela inicial ou por um contrato de ativação ou quando é iniciado por outro processo ou método. Você também atrasa o início do aplicativo quando deseja depurar uma tarefa em segundo plano quando o aplicativo em si não está em execução.  
  
 Para atrasar a inicialização do aplicativo, você pode fazer o seguinte:  
  
-   Para aplicativos Visual c# e Visual Basic, selecione **não iniciar, mas depurar meu código quando iniciar** no **depurar** página de propriedades.  
  
-   Para aplicativos Visual C++ e JavaScript, escolha **Sim** do **Iniciar aplicativo** lista o **depuração** página de propriedades.  
  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a>(Opcional) Desabilitar loopbacks de rede  
  
 Por motivos de segurança, um aplicativo UWP instalado da maneira padrão não é permitido para fazer chamadas de rede para o dispositivo que está instalado. Por padrão, a implantação do Visual Studio cria uma isenção dessa regra para o aplicativo implantado. Essa isenção permite que você teste procedimentos de comunicação em um único computador. Antes de enviar seu aplicativo para Microsoft Store, você deve testar seu aplicativo sem a isenção.  
  
 Para remover a isenção de loopback de rede:  
  
-   Para aplicativos Visual c# e Visual Basic, desmarque o **permitir loopback de rede local** caixa de seleção de **depurar** página de propriedades.  
  
-   Para aplicativos Visual C++ e JavaScript, escolha **não** do **permitir Loopback de rede Local** lista o **depuração** página de propriedades.  
  
###  <a name="BKMK__Optional__Reinstall_the_app_when_you_start_debugging"></a>(Opcional) Reinstale o aplicativo ao iniciar a depuração  
 Para diagnosticar problemas com a instalação e configuração inicial do seu aplicativo do Visual c# ou Visual Basic, escolha **desinstalar e reinstalar meu pacote** no **depurar** página de propriedades para recriar um instalação original ao iniciar a depuração. Essa opção não está disponível para projetos em Visual C++ e JavaScript.  
  
###  <a name="BKMK__Optional__Disable_authentication_requirement_to_start_the_remote_debugger"></a>(Opcional) Desativar a requisição de autenticação para iniciar o depurador remoto  
  
 Por padrão, você deve fornecer credenciais para executar o depurador remoto quando você seleciona **máquina remota** como o destino de implantação.
  
> [!IMPORTANT]
>  Você pode optar por executar o depurador remoto sem autenticação, mas isso é altamente desaconselhável. Nesse modo não há nenhuma segurança de rede. Escolha sem autenticação somente se você tiver certeza de que a rede não está em risco de um código mal-intencionado ou tráfego hostil.  
  
 Para remover a requisição de autenticação:  
  
1.  Para aplicativos Visual c# e Visual Basic, selecione **máquina remota** como o **dispositivo de destino** no **depurar** página de propriedades e defina **modo de autenticação**  para **nenhum** ou **Universal (protocolo não criptografado)**.
  
2.  Para aplicativos Visual C++ e JavaScript, selecione **máquina remota** como o **dispositivo de destino** no **depuração** página de propriedades e defina **exigem Autenticação** para **nenhum** ou **Universal (protocolo não criptografado)**.  

    **Universal (protocolo não criptografado)** é para uso quando você estiver implantando em um dispositivo remoto. Atualmente, isso é para dispositivos IoT, Xbox dispositivos e HoloLens dispositivos, bem como os criadores de atualização ou computadores mais recentes. Universal (protocolo não criptografado) deve ser usado somente em redes confiáveis. A conexão de depuração é vulnerável a usuários mal-intencionados que podem interceptar e alterar dados passados entre o desenvolvimento e o computador remoto.  
  
##  <a name="BKMK_Start_the_debugging_session"></a>Iniciar a sessão de depuração  
  
###  <a name="BKMK_Start_debugging__F5_"></a>Iniciar a depuração (F5)  
 Quando você escolhe **iniciar depuração** (teclado: F5) sobre o **depurar** menu, o Visual Studio inicia o aplicativo com o depurador anexado. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção ou o aplicativo chegue ao fim.  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Iniciar a depuração (F5), mas atrasar o início do aplicativo  
 Você pode definir que o aplicativo seja executado no modo de depuração, mas inicie-o por outro método que não seja o depurador. Por exemplo, convém depurar a inicialização do aplicativo no menu Iniciar ou depurar um processo em segundo plano no aplicativo sem iniciar o aplicativo. Para atrasar o início do aplicativo, faça o seguinte:  
  
-   Sobre o **depurar** página de propriedades do aplicativo (**depuração** em Visual C++ e JavaScript)  
  
    -   Para aplicativos Visual c# e Visual Basic, escolha **não iniciar, mas depurar meu código quando iniciar**.  
  
    -   Para aplicativos Visual C++ e JavaScript, escolha **Sim** do **Iniciar aplicativo** lista.  
  
-   Escolha **iniciar depuração** no **depurar** menu (teclado: F5).  
  
-   Inicie o aplicativo pelo menu Iniciar, por um contrato de execução ou por outro procedimento.  
  
 O aplicativo é iniciado no modo de depuração. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao fim.  
  
 . Para obter mais informações sobre como depurar tarefas em segundo plano, consulte [gatilho suspender, continuar e eventos para aplicativos UWP em segundo plano)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
###  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Iniciar um aplicativo instalado no depurador  
Quando você inicia a depuração usando F5, o Visual Studio compila e implanta o aplicativo, define que ele seja executado no modo de depuração e, em seguida, inicia-o. Para iniciar um aplicativo que já está instalado em um dispositivo, use o **depurar pacote do aplicativo instalado** caixa de diálogo. Esse procedimento é útil quando você precisa depurar um aplicativo que foi instalado da Microsoft Store ou quando você tem os arquivos de origem para o aplicativo, mas você não tem um projeto do Visual Studio para o aplicativo. Por exemplo, você pode ter um sistema de build personalizado que não use projetos ou soluções do Visual Studio.  
  
O aplicativo pode ser instalado no dispositivo local ou pode estar localizado em um dispositivo remoto.  É possível iniciar o aplicativo imediatamente ou defini-lo para ser executado no depurador quando for iniciado por outro processo ou método, por exemplo, no menu Iniciar ou por um contrato de ativação. Você também pode definir o aplicativo para ser executado no modo de depuração quando quiser depurar um processo em segundo plano sem iniciar o aplicativo. Para obter mais informações, consulte [gatilho suspender, continuar e eventos para aplicativos UWP em segundo plano)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
Para iniciar um aplicativo instalado no depurador, escolha **depurar**, em seguida, **outros destinos de depuração**e, em seguida, **depurar pacote do aplicativo instalado**. Para obter instruções adicionais, consulte [depurar um pacote de aplicativos instalados](../debugger/debug-installed-app-package.md).

> [!NOTE]
> Para Windows 8.1, escolha **depurar**e, em seguida, escolha **depurar pacote do aplicativo instalado**.

###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Anexar o depurador a um aplicativo UWP em execução  

Para depurar um aplicativo UWP em execução, escolha **depurar**, em seguida, **outros destinos de depuração**e, em seguida, **depurar pacote do aplicativo instalado**. Para obter instruções adicionais, consulte [depurar um pacote de aplicativos instalados](../debugger/debug-installed-app-package.md).
  
###  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Anexar o depurador a um aplicativo de 8. x do Windows em execução
 Para anexar o depurador a um aplicativo [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)], você deve usar o Gerenciador de Pacotes Depuráveis para definir a execução do aplicativo no modo de depuração. O recurso é instalado com as ferramentas remotas para Visual Studio.  
  
 Anexar o depurador a um aplicativo é útil quando você precisa depurar um aplicativo já instalado; por exemplo, um que tenha sido instalado da [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]. A anexação é necessária quando você tem os arquivos de origem do aplicativo, mas não tem um projeto do Visual Studio para ele. Por exemplo, você pode ter um sistema de build personalizado que não use projetos ou soluções do Visual Studio.  
  
 Para anexar o depurador a um aplicativo, são necessárias as seguintes etapas:  
  
1.  Defina o aplicativo para ser executado no modo de depuração. Isso deve ser feito quando o aplicativo não está em execução.  
  
2.  Inicie o aplicativo. Você pode fazer isso pela tela inicial, por um contrato de execução ou por outro método.  
  
3.  Anexe o depurador ao aplicativo em execução.  
  
####  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Definir o aplicativo para ser executado no modo de depuração  
  
1.  Instale as ferramentas remotas para Visual Studio no dispositivo em que o aplicativo está instalado. Consulte [instalando as ferramentas remotas](../debugger/remote-debugging.md).  
  
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

    > [!NOTE]
    >  Ao contrário de outros tipos de aplicativo, os aplicativos JavaScript são executados em uma instância do processo wwahost.exe. Se outros aplicativos JavaScript estiverem em execução quando você anexa ao aplicativo, será necessário saber a ID do processo numérico (PID) do wwahost.exe em que o aplicativo está executando.  
    >   
    >  A maneira mais fácil de lidar com essa situação é fechar todos os outros aplicativos JavaScript. Do contrário, você pode abrir o Gerenciador de Tarefas do Windows antes de iniciar o aplicativo e observar as IDs dos processos wwahost.exe. Quando você especifica o processo para anexar no **processos disponíveis** caixa de diálogo, o wwahost.exe do aplicativo terá uma id diferente daquelas que você observou.  
  
5.  Escolha **anexar**.  
  
 O Visual Studio anexa o depurador ao processo. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao fim.  
  
## <a name="see-also"></a>Consulte também  
 [Depurar aplicativos no Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)   