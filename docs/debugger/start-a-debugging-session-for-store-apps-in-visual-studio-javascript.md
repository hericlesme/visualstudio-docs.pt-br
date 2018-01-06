---
title: "Iniciar uma sessão de depuração para aplicativos UWP no Visual Studio (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.error.wwahost_scriptdebuggingdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: fb91203f-2cf4-44d3-8ed9-93bc5aaa50b8
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: b92f2f5ac10f917257e58443ab2161a164f39b28
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="start-a-debugging-session-for-uwp-apps-in-visual-studio-javascript"></a>Iniciar uma sessão de depuração para aplicativos UWP no Visual Studio (JavaScript)
![Aplica-se a Windows e Windows Phone](../debugger/media/windows_and_phone_content.png "windows_and_phone_content")  
  
 Este tópico descreve como iniciar uma sessão de depuração para aplicativos UWP gravados em JavaScript e HTML5. Você pode iniciar a depuração com um único pressionamento de tecla ou configurar a sessão de depuração para cenários específicos e escolher a maneira de iniciar o aplicativo.  
  
> [!NOTE]
>  Para aplicativos escritos em XAML e Visual c#, Visual C++ ou Visual Basic, consulte [iniciar uma sessão de depuração (VB, c#, C++ e XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_In_this_topic"></a> Neste tópico  
 [Neste tópico](#BKMK_In_this_topic)  
  
 [A maneira fácil de iniciar a depuração](#BKMK_The_easy_way_to_start_debugging)  
  
 [Configurar a sessão de depuração](#BKMK_Configure_the_debugging_session)  
  
-   [Abra a página de propriedades de depuração para o projeto](#BKMK_Open_the_debugging_property_page_for_the_project)  
  
-   [Escolher opções de configuração de compilação](#BKMK_Choose_the_build_configuration_options)  
  
-   [Escolha o destino de implantação](#BKMK_Choose_the_deployment_target)  
  
-   [Escolher o depurador a ser usado](#BKMK_Choose_the_debugger_to_use)  
  
-   [(Opcional) Atrasar o início do aplicativo na sessão de depuração](#BKMK__Optional__Delay_starting_app_in_the_debug_session)  
  
-   [(Opcional) Desabilitar loopbacks de rede](#BKMK__Optional__Disable_network_loopbacks)  
  
 [Iniciar a sessão de depuração](#BKMK_Start_the_debugging_session)  
  
-   [Iniciar a depuração (F5)](#BKMK_Start_debugging__F5_)  
  
-   [Iniciar a depuração (F5), mas atrasar o início do aplicativo](#BKMK_Start_debugging__F5__but_delay_the_app_start)  
  
 [Iniciar um aplicativo instalado no depurador](#BKMK_Start_an_installed_app_in_the_debugger)  
  
 [Anexar o depurador a um aplicativo em execução](#BKMK_Attach_the_debugger_to_a_running_app_)  
  
-   [Definir o aplicativo para ser executado no modo de depuração](#BKMK_Set_the_app_to_run_in_debug_mode)  
  
-   [Anexar o depurador](#BKMK_Attach_the_debugger)  
  
##  <a name="BKMK_The_easy_way_to_start_debugging"></a>A maneira fácil de iniciar a depuração  
 ![Aplica-se apenas ao Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
1.  Abra a solução do aplicativo no Visual Studio.  
  
2.  Se a solução contiver vários projetos, certifique-se de que o projeto que você deseja depurar é o projeto de inicialização. No Gerenciador de soluções, selecione o projeto e, em seguida, escolha **definir como projeto de inicialização** no menu de contexto.  
  
3.  Pressione F5.  
  
 ![Aplica-se apenas ao Windows Phone](../debugger/media/phone_only_content.png "phone_only_content")  
  
 O Visual Studio compila e inicia o aplicativo com o depurador anexado. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao fim. Para obter mais informações, consulte [início rápido: depurar HTML e CSS](../debugger/quickstart-debug-html-and-css.md).  
  
##  <a name="BKMK_Configure_the_debugging_session"></a>Configurar a sessão de depuração  
 Como o script não está compilado, a configuração de build e as configurações da plataforma não se aplicam. Se você estiver depurando um componente C++ ou gerenciado, defina o **configuração** para **depurar** e escolha sua plataforma de destino do **configuração** caixa de diálogo.  
  
###  <a name="BKMK_Open_the_debugging_property_page_for_the_project"></a>Abra a página de propriedades de depuração para o projeto  
  
1.  No Gerenciador de Soluções, selecione o projeto. No menu de atalho, escolha **propriedades**.  
  
2.  Expanda o **propriedades de configuração** nó e, em seguida, escolha **depuração**.  
  
###  <a name="BKMK_Choose_the_build_configuration_options"></a>Escolher opções de configuração de compilação  
  
1.  Do **configuração** , escolha **depurar** ou **(ativo) depurar**.  
  
2.  Do **plataforma** lista escolha a plataforma de destino do build. Na maioria dos casos, **qualquer CPU** é a melhor opção.  
  
###  <a name="BKMK_Choose_the_deployment_target"></a>Escolha o destino de implantação  
 Você pode implantar e depurar um aplicativo no computador com o Visual Studio, no simulador do Visual Studio do computador local ou de um computador remoto. Escolha o destino do **depurador a iniciar** lista o **depuração** página de propriedades do projeto.  
  
 ![Aplica-se apenas ao Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 Para um aplicativo UWP, escolha uma das seguintes opções do **dispositivo de destino** lista:  
  
|||  
|-|-|  
|**Computador local**|Depura o aplicativo na sessão atual no computador local. Consulte [UWP executar aplicativos no computador local](../debugger/run-windows-store-apps-on-the-local-machine.md).|  
|**Simulador**|Depura o aplicativo no simulador do Visual Studio para aplicativos [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]. O simulador é uma janela da área de trabalho que permite depurar recursos, como gestos de toque e rotação de dispositivos, que não estão disponíveis no computador local. Consulte [UWP executar aplicativos no simulador](../debugger/run-windows-store-apps-in-the-simulator.md).|  
|**Computador remoto**|Depura o aplicativo em um dispositivo conectado ao computador local por uma intranet ou diretamente por meio de um cabo Ethernet. Para depurar remotamente, as Ferramentas Remotas do Visual Studio devem estar instaladas e em execução no dispositivo remoto. Consulte [UWP executar aplicativos em um computador remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md).|  
  
 Se você escolher **máquina remota**, especifique o nome ou endereço IP do computador remoto em uma das seguintes maneiras:  
  
-   Digite o nome ou endereço IP do computador remoto no **nome da máquina** caixa.  
  
-   Clique na seta para baixo no **nome da máquina** caixa e escolha  **\<localizar... >**. Em seguida, escolha o computador remoto na **Selecionar Conexão de depurador remoto** caixa de diálogo.  
  
     ![Selecione a Conexão de depurador remoto](../debugger/media/vsrun_pro_selectremotedebuggerdlg.png "VSRUN_PRO_SelectRemoteDebuggerDlg")  
  
    > [!NOTE]
    >  A caixa de diálogo Selecionar Conexão de Depurador Remoto exibe os computadores que estão na sub-rede local e os computadores que estão diretamente conectados ao computador com o Visual Studio por um cabo Ethernet. Para especificar outro computador, digite o nome no **nome da máquina** caixa.  
  
 ![Aplica-se apenas ao Windows Phone](../debugger/media/phone_only_content.png "phone_only_content")  
  
 Para um aplicativo do Windows Phone, escolha **dispositivo** ou um dos emuladores do **dispositivo de destino** lista.  
  
###  <a name="BKMK_Choose_the_debugger_to_use"></a>Escolher o depurador a ser usado  
 Por padrão, o depurador se anexa ao código JavaScript do aplicativo. Você pode escolher depurar o código C++ nativo e gerenciado dos componentes do aplicativo em vez do código JavaScript. Especifique o código para depurar o **tipo de depurador** lista o **depuração** página de propriedades do projeto de aplicativo.  
  
 Escolha um destes depuradores das **tipo de depurador** lista:  
  
|||  
|-|-|  
|**Somente script**|Depura o código JavaScript no aplicativo. O código gerenciado e o código nativo são ignorados.|  
|**Somente nativo**|Depura o código C/C++ nativo no aplicativo. O código gerenciado e o código JavaScript são ignorados.|  
|**Nativo com Script**|Depura o código C++ nativo e o código JavaScript no aplicativo.|  
|**Somente gerenciado**|Depura o código gerenciado no aplicativo. O código JavaScript e o código C/C++ nativo são ignorados.|  
|**Misto (gerenciado e nativo)**|Depura o código C/C++ nativo e o código gerenciado no aplicativo. O código JavaScript é ignorado.|  
  
###  <a name="BKMK__Optional__Delay_starting_app_in_the_debug_session"></a>(Opcional) Atrasar o início do aplicativo na sessão de depuração  
 Por padrão, o Visual Studio inicia o aplicativo imediatamente quando você começa a depuração. Você também pode iniciar uma sessão de depuração, mas atrasar o início do seu aplicativo. O aplicativo é iniciado no depurador quando é iniciado do menu Iniciar ou por um contrato de ativação ou quando é iniciado por outro processo ou método. Você também pode usar o início atrasado para depurar eventos em segundo plano no aplicativo que você quer que ocorram quando o aplicativo não está em execução.  
  
 Especifique se deseja atrasar a inicialização do seu aplicativo no **Iniciar aplicativo** lista o **depuração** página de propriedades do projeto de aplicativo. Escolha uma destas opções:  
  
-   Escolha **não** para atrasar a inicialização do aplicativo.  
  
-   Escolha **Sim** para iniciar o aplicativo imediatamente.  
  
###  <a name="BKMK__Optional__Disable_network_loopbacks"></a>(Opcional) Desabilitar loopbacks de rede  
 ![Aplica-se apenas ao Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 Por motivos de segurança, um aplicativo UWP instalado da maneira padrão não é permitido para fazer chamadas de rede para o dispositivo que está instalado. Por padrão, a implantação do Visual Studio cria uma isenção dessa regra para o aplicativo implantado. Essa isenção permite que você teste procedimentos de comunicação em um único computador. Antes de enviar seu aplicativo para Microsoft Store, você deve testar seu aplicativo sem a isenção.  
  
 Para remover a isenção de loopback de rede, escolha **não** do **permitir Loopback de rede** lista o **depuração** página de propriedades.  
  
##  <a name="BKMK_Start_the_debugging_session"></a>Iniciar a sessão de depuração  
  
###  <a name="BKMK_Start_debugging__F5_"></a>Iniciar a depuração (F5)  
 Quando você escolhe **iniciar depuração** no **depurar** menu (teclado: F5), o Visual Studio inicia o aplicativo com o depurador anexado. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao fim.  
  
###  <a name="BKMK_Start_debugging__F5__but_delay_the_app_start"></a>Iniciar a depuração (F5), mas atrasar o início do aplicativo  
 Você pode definir o aplicativo para ser executado no modo de depuração, mas inicie-o por outro método que não seja o depurador. Por exemplo, convém depurar a inicialização do aplicativo no menu Iniciar ou depurar um processo em segundo plano do aplicativo sem iniciá-lo. Para atrasar o início do aplicativo, faça o seguinte:  
  
1.  Sobre o **depurar** página do aplicativo propriedades do projeto, escolha **não** do **Iniciar aplicativo** lista.  
  
2.  Escolha **iniciar depuração** no **depurar** menu (teclado: F5).  
  
3.  Inicie o aplicativo pelo menu Iniciar, por um contrato de execução ou por outro procedimento.  
  
 O aplicativo é iniciado no modo de depuração. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao fim.  
  
 . Para obter mais informações sobre como depurar tarefas em segundo plano, consulte [gatilho suspender, continuar e eventos para aplicativos UWP em segundo plano)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
##  <a name="BKMK_Start_an_installed_app_in_the_debugger"></a>Iniciar um aplicativo instalado no depurador  
 Quando você inicia a depuração usando F5, o Visual Studio compila e implanta o aplicativo, define que ele seja executado no modo de depuração e, em seguida, inicia-o. Para iniciar um aplicativo que já está instalado em um dispositivo, use a caixa de diálogo Depurar Pacote do Aplicativo Instalado. Esse procedimento é útil quando você precisa depurar um aplicativo instalado da Windows Store ou quando você tem os arquivos de origem do aplicativo, mas não tem um projeto do Visual Studio para o aplicativo. Por exemplo, você pode ter um sistema de build personalizado que não use projetos ou soluções do Visual Studio.  
  
 O aplicativo pode ser instalado no dispositivo local ou pode estar localizado em um dispositivo remoto.  É possível iniciar o aplicativo imediatamente ou defini-lo para ser executado no depurador quando for iniciado por outro processo ou método, por exemplo, no menu Iniciar ou por um contrato de ativação. Você também pode definir o aplicativo para ser executado no modo de depuração quando quiser depurar um processo em segundo plano sem iniciar o aplicativo. Para obter mais informações, consulte [gatilho suspender, continuar e eventos para aplicativos UWP em segundo plano)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md).  
  
 Para definir um aplicativo instalado para ser executado no modo de depuração, faça o seguinte:  
  
> [!NOTE]
>  O aplicativo não deve estar em execução quando você iniciar este procedimento.  
  
1.  Sobre o **depurar** menu, escolha **depurar pacote do aplicativo instalado**.  
  
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
  
##  <a name="BKMK_Attach_the_debugger_to_a_running_app_"></a>Anexar o depurador a um aplicativo em execução  
 Para anexar o depurador a um aplicativo [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)], você deve usar o Gerenciador de Pacotes Depuráveis para definir a execução do aplicativo no modo de depuração. Esse recurso é instalado com as Ferramentas Remotas do Visual Studio.  
  
 Anexar o depurador a um aplicativo é útil quando você precisa depurar um aplicativo já instalado; por exemplo, um que tenha sido instalado na Windows Store. A anexação é necessária quando você tem os arquivos de origem do aplicativo, mas não tem um projeto do Visual Studio para ele. Por exemplo, você pode ter um sistema de build personalizado que não use projetos ou soluções do Visual Studio.  
  
 Para anexar a um aplicativo:  
  
1.  Defina o aplicativo para ser executado no modo de depuração. Isso deve ser feito quando o aplicativo não está em execução.  
  
2.  Inicie o aplicativo. Você pode iniciar o aplicativo do menu Iniciar por um contrato de execução ou por outro método.  
  
3.  Anexe o depurador ao aplicativo em execução.  
  
###  <a name="BKMK_Set_the_app_to_run_in_debug_mode"></a>Definir o aplicativo para ser executado no modo de depuração  
  
1.  Instale as Ferramentas Remotas do Visual Studio no dispositivo em que o aplicativo está instalado. Consulte [instalando as ferramentas remotas](http://msdn.microsoft.com/library/windows/apps/hh441469.aspx#BKMK_Installing_the_Remote_Tools).  
  
2.  No menu Iniciar, procure por `Debuggable Package Manager` e inicie-o.  
  
     É exibida uma janela do PowerShell corretamente configurada para o cmdlet AppxDebug.  
  
3.  Para habilitar a depuração de um aplicativo, é preciso especificar o identificador NomeCompletodoPacote do aplicativo. Para ver uma lista de todos os aplicativos que incluem o NomeCompletodoPacote, digite `Get-AppxPackage` no aviso do PowerShell.  
  
4.  No prompt do PowerShell, digite `Enable-AppxDebug` *PackageFullName* onde *PackageFullName* é o identificador PackageFullName do aplicativo.  
  
###  <a name="BKMK_Attach_the_debugger"></a>Anexar o depurador  
  
> [!TIP]
>  Os aplicativos JavaScript são executados em uma instância do processo wwahost.exe. Se outros aplicativos JavaScript estiverem em execução quando você anexa ao aplicativo, será necessário saber a ID do processo numérico (PID) do wwahost.exe em que o aplicativo está executando.  
>   
>  A maneira mais fácil de lidar com essa situação é fechar todos os outros aplicativos JavaScript. Do contrário, você pode abrir o Gerenciador de Tarefas do Windows antes de iniciar o aplicativo e observar as IDs dos processos wwahost.exe. Quando você especifica o processo para anexar no **processos disponíveis** caixa de diálogo, o wwahost.exe do aplicativo terá uma id diferente daquelas que você observou.  
  
 Para anexar o depurador:  
  
1.  Sobre o **depurar** menu, escolha **anexar ao processo**.  
  
     O **anexar ao processo** caixa de diálogo é exibida.  
  
2.  Para anexar a um aplicativo em um dispositivo remoto, especifique o dispositivo remoto no **qualificador** caixa. Você pode:  
  
    -   Digite o nome no **qualificador** caixa.  
  
    -   Escolha a seta para baixo no **qualificador** caixa e escolha o dispositivo em uma lista de dispositivos que você já anexou antes.  
  
    -   Escolha **localizar** para escolher o dispositivo em uma lista de dispositivos em sua sub-rede local.  
  
3.  Especifique o tipo de código que você deseja depurar no **anexar a** caixa.  
  
     Escolha **selecione** e, em seguida, faça o seguinte:  
  
    -   Escolha **determinar automaticamente o tipo de código para depurar**.  
  
    -   Escolha **depurar esses tipos de código** e, em seguida, escolha um ou mais tipos na lista.  
  
4.  No **processos disponíveis** , escolha apropriada **wwahost.exe** processo. Use o **título** coluna para identificar seu aplicativo.  
  
5.  Escolha **anexar**.  
  
 O Visual Studio anexa o depurador ao processo. A execução continua até que um ponto de interrupção seja alcançado, você suspenda a execução manualmente, ocorra uma exceção sem tratamento ou o aplicativo chegue ao fim.  
  
## <a name="see-also"></a>Consulte também  
 [Controlar a execução em uma sessão de depuração (JavaScript)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)   
 [Início rápido: Depurar HTML e CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Disparar suspender, continuar e eventos para aplicativos UWP em segundo plano)](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)   
 [Depurar aplicativos no Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)