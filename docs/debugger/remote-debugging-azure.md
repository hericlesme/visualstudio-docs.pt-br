---
title: Remoto depurar Core de ASP.NET no IIS e o Azure | Microsoft Docs
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: fc8e657f6fb67884bd12de3f8e65c78077fa9b2e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio-2017"></a>Depuração remota ASP.NET Core no IIS no Azure no Visual Studio de 2017

Este guia explica como configurar e configurar um aplicativo do Visual Studio 2017 ASP.NET Core, implantá-lo no IIS usando o Azure e anexar o depurador remoto do Visual Studio.

A maneira recomendada para depuração remota no Azure depende de seu cenário:

* Para depurar ASP.NET Core no serviço de aplicativo do Azure, consulte [aplicativos Azure depurar usando o depurador do instantâneo](../debugger/debug-live-azure-applications.md). Esse é o método recomendado.
* Para depurar ASP.NET Core no serviço de aplicativo do Azure usando os recursos de depuração mais tradicionais, execute as etapas neste tópico (consulte a seção [de depuração remota no serviço de aplicativo do Azure](#remote_debug_azure_app_service)).

    Nesse cenário, você deve implantar seu aplicativo do Visual Studio no Azure, mas você não precisa instalar manualmente ou configurar o IIS ou o depurador remoto (esses componentes são representados por linhas pontilhadas), conforme mostrado na ilustração a seguir.

    ![Componentes do depurador remoto](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Para depurar o IIS em uma VM do Azure, siga as etapas neste tópico (consulte a seção [depuração remota em uma VM do Azure](#remote_debug_azure_vm)). Isso permite que você use uma configuração personalizada do IIS, mas as etapas de instalação e implantação estão mais complicadas.

    Para uma VM do Azure, você deve implantar seu aplicativo do Visual Studio para o Azure e você também precisará instalar manualmente a função do IIS e o depurador remoto, conforme mostrado na ilustração a seguir.

    ![Componentes do depurador remoto](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Para depurar ASP.NET Core no Service Fabric do Azure, consulte [depurar um aplicativo de malha do serviço remoto](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Certifique-se de excluir os recursos do Azure que você cria quando você concluiu as etapas neste tutorial. Dessa forma, que você pode evitar incorrer em encargos desnecessários.


### <a name="requirements"></a>Requisitos

Não há suporte para a depuração entre dois computadores conectados por meio de um proxy. Depuração em uma conexão de baixa largura de banda, como dial-up da Internet, ou de alta latência, ou pela Internet entre países não é recomendado e pode falhar ou ser muito lento. Para obter uma lista completa dos requisitos, consulte [requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Criar o aplicativo do ASP.NET Core no computador Visual Studio de 2017 

1. Crie um novo aplicativo ASP.NET Core. (Escolha **arquivo > Novo > projeto**, em seguida, selecione **Visual C# > Web > aplicativo Web do ASP.NET Core**).

    No **ASP.NET Core** seção de modelos, selecione **aplicativo Web**.

2. Verifique se **ASP.NET Core 2.0** for selecionada, que **Habilitar suporte de Docker** é **não** selecionado e que **autenticação** é definido como **Nenhuma autenticação**.

3. Nomeie o projeto **MyASPApp** e clique em **Okey** para criar a nova solução.

4. Abra o arquivo About.cshtml.cs e definir um ponto de interrupção no `OnGet` método (em modelos mais antigos, abra o HomeController em vez disso e defina o ponto de interrupção `About()` método).

## <a name="remote_debug_azure_app_service"></a> Depuração remota ASP.NET Core em um serviço de aplicativo do Azure

No Visual Studio, você pode publicar e depurar seu aplicativo para uma instância totalmente provisionado do IIS rapidamente. No entanto, a configuração do IIS é predefinida e não é possível personalizá-lo. Para obter instruções mais detalhadas, consulte [implantar um aplicativo web do ASP.NET Core para o Azure usando o Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Se você precisa da capacidade de personalizar o IIS, tente depuração um [VM do Azure](#BKMK_azure_vm).) 

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>Para implantar o aplicativo e a depuração remota usando o Gerenciador de servidores

1. No Visual Studio, clique com botão direito no nó do projeto e escolha **publicar**.

2. Escolha **serviço de aplicativo do Microsoft Azure** do **publicar** caixa de diálogo, selecione **criar novo**e siga os prompts para publicar.

    Para obter instruções detalhadas, consulte [implantar um aplicativo web do ASP.NET Core para o Azure usando o Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

3. Abra **Server Explorer** (**exibição** > **Server Explorer**), com o botão direito na instância do serviço de aplicativo e escolha **Anexar depurador**.

4. No aplicativo ASP.NET em execução, clique no link para o **sobre** página.

    O ponto de interrupção deve ser atingido no Visual Studio.

    É só isso! O restante das etapas neste tópico se aplicam a depuração remota em uma VM do Azure.

## <a name="remote_debug_azure_vm"></a> Depuração remota ASP.NET Core em uma VM do Azure

Você pode criar uma VM do Azure para o Windows Server e, em seguida, instalar e configurar o IIS e outros componentes de software necessárias. Isso leva mais tempo que a implantação para um serviço de aplicativo do Azure e requer que você siga as etapas restantes neste tutorial.

Primeiro, siga todas as etapas descritas em [instalar e executar o IIS](/azure/virtual-machines/virtual-machines-windows-hero-role).

Quando você abre a porta 80 no grupo de segurança de rede, também abra a porta 4022 para o depurador remoto. Dessa forma, você não precisará abri-lo mais tarde.

### <a name="update-browser-security-settings-on-windows-server"></a>Atualizar configurações de segurança do navegador no Windows Server

Dependendo de suas configurações de segurança do navegador, isso pode economizar tempo para adicionar os seguintes sites confiáveis no seu navegador para que você pode facilmente baixar o software descrito neste tutorial. Acesso a esses sites pode ser necessários:

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- visualstudio.com

Se você estiver usando o Internet Explorer, você pode adicionar sites confiáveis, vá para **opções da Internet > Segurança > Sites confiáveis > Sites**. Essas etapas são diferentes para outros navegadores. (Se você precisar baixar uma versão mais antiga do depurador remoto do my.visualstudio.com, alguns sites confiáveis adicionais são necessário para entrar.)

Quando você baixar o software, você pode receber solicitações para conceder a permissão para carregar vários scripts do site da web e recursos. Na maioria dos casos, esses recursos adicionais não são necessários para instalar o software.

### <a name="install-aspnet-core-on-windows-server"></a>Instalar o ASP.NET Core no Windows Server

1. Instalar o [hospedagem do .NET Core Windows Server](https://aka.ms/dotnetcore-2-windowshosting) pacote no sistema de hospedagem. O pacote instalará o .NET Core Runtime, biblioteca principal do .NET e o módulo do ASP.NET Core. Para obter mais instruções detalhadas, consulte [publicar no IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Se o sistema não tiver uma conexão de Internet, obtenha e instale o *[Microsoft Visual C++ 2015 redistribuível](https://www.microsoft.com/download/details.aspx?id=53840)* antes de instalar o pacote de hospedagem do .NET Core Windows Server.

3. Reiniciar o sistema (ou execute **net stop foi /y** seguido por **net start-w3svc** em um prompt de comando para acompanhar uma alteração no caminho do sistema).

### <a name="BKMK_install_webdeploy"></a> (Opcional) Instalar Web implantar 3.6 no Windows Server

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

### <a name="BKMK_deploy_asp_net"></a> Configurar o site da Web ASP.NET no computador Windows Server

1. Abra o **serviços de informações da Internet (IIS) Manager** e vá para **Sites**.

2. Clique com botão direito do **Default Web Site** nó e selecione **Adicionar aplicativo**.

3. Definir o **Alias** campo **MyASPApp** e o campo de pool de aplicativos para **sem código gerenciado**. Definir o **caminho físico** para **C:\Publish** (onde você irá implantar posteriormente o projeto ASP.NET).

4. Com o site selecionado no Gerenciador do IIS, escolha **editar permissões**e certifique-se de que IUSR, IIS_IUSRS ou o usuário configurado para o Pool de aplicativos é um usuário autorizado com direitos de leitura e execução.

    Se você não vir um desses usuários com acesso, percorrer as etapas para adicionar IUSR como um usuário com direitos de leitura e execução.

### <a name="bkmk_webdeploy"></a> (Opcional) Publicar e implantar o aplicativo usando a implantação da Web do Visual Studio

Se você instalou a implantação da Web usando o Web Platform Installer, você pode implantar o aplicativo diretamente do Visual Studio.

1. Inicie o Visual Studio com privilégios elevados e reabra o projeto.

    Isso pode ser necessário para implantar seu aplicativo usando a implantação da Web.

2. No **Solution Explorer**, com o botão direito no nó do projeto e selecione **publicar**.

3. Para **selecionar um destino de publicação**, selecione **Máquina Virtual do Microsoft Azure** e clique em **publicar**.

    ![RemoteDBG_Publish_IISl](../debugger/media/remotedbg_azure_vm_profile.png "RemoteDBG_Publish_IIS")

4. Na caixa de diálogo, selecione a máquina virtual do Azure que você criou anteriormente.

4. Insira os parâmetros de configuração de correção para a configuração de máquina virtual do Azure e o IIS.

    ![RemoteDBG_Publish_WebDeployl](../debugger/media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Se um nome de host não resolver ao tentar validar na próxima etapas no **Server** texto caixa, tente o endereço IP. Verifique se você usa a porta 80 no **Server** texto caixa e certifique-se de que a porta 80 está aberta no firewall.

6. Clique em **próximo**, escolha um **depurar** configuração e escolha **remover arquivos adicionais no destino** sob o **Publicar arquivo** Opções.

5. Clique em **Prev**e, em seguida, escolha **validar**. Se a configuração de conexão for validado, você pode tentar publicar.

6. Clique em **publicar** para publicar o aplicativo.

    A guia saída mostrará se a publicação foi bem-sucedida e o navegador abrirá o aplicativo.

    Se você receber um erro mencionar a implantação da Web, verifique novamente as etapas de instalação de implantação da Web e verifique se o [correto de portas estão abertas](#bkmk_openports) estão no servidor.

    Se o aplicativo implanta com êxito, mas não funcionar corretamente, verifique novamente se o IIS e o projeto do Visual Studio usando a mesma versão do ASP.NET. Se isto é não o problema, pode haver um problema com a configuração do IIS ou a configuração de site da Web. No Windows Server, abra o site da Web do IIS para mensagens de erro mais específicas e, em seguida, verifique novamente as etapas anteriores.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Opcional) Publicar e implantar o aplicativo pela publicação em uma pasta local do Visual Studio

Se você não estiver usando a implantação da Web, você deve publicar e implantar o aplicativo usando o sistema de arquivos ou outras ferramentas. Você pode começar criando um pacote usando o sistema de arquivos e, em seguida, implantar o pacote manualmente ou usar outras ferramentas, como XCopy, RoboCopy ou PowerShell. Nesta seção, vamos supor que são copiar manualmente o pacote, se você não estiver usando a implantação da Web.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a> Baixe e instale as ferramentas remotas no Windows Server

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Configurar o depurador remoto no Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se você precisa adicionar permissões para usuários adicionais, alterar o modo de autenticação ou número da porta para o depurador remoto, consulte [configurar o depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a> Anexar ao aplicativo ASP.NET de computador do Visual Studio

1. No computador do Visual Studio, abra o **MyASPApp** solução.
2. No Visual Studio, clique em **Depurar > Anexar ao processo** (Ctrl + Alt + P).

    > [!TIP]
    > No Visual Studio de 2017, você pode anexar novamente para o mesmo processo anteriormente conectados a usando **Depurar > anexe ao processo...** (Shift + Alt + P). 

3. Defina o campo do qualificador  **\<nome do computador remoto >: 4022**.
4. Clique em **atualizar**.
    Você deve ver alguns processos que aparecem no **processos disponíveis** janela.

    Se você não vir todos os processos, tente usar o endereço IP em vez do nome do computador remoto (a porta é necessária). Você pode usar `ipconfig` em uma linha de comando para obter o endereço IPv4.

    Se você quiser usar o **localizar** botão, talvez você precise [abra a porta UDP 3702](#bkmk_openports) no servidor.

5. Verificar **Mostrar processos de todos os usuários**.
6. Digite a primeira letra de um nome de processo para localizar rapidamente **dotnet.exe** (para ASP.NET Core).
    >Observação: Para um aplicativo ASP.NET Core, o nome do processo anterior foi dnx.exe.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Clique em **Anexar**.

8. Abra o site do computador remoto. Em um navegador, vá para **http://\<nome do computador remoto >**.
    
    Você verá a página da web ASP.NET.
9. No aplicativo ASP.NET em execução, clique no link para o **sobre** página.

    O ponto de interrupção deve ser atingido no Visual Studio.

### <a name="bkmk_openports"></a> Solução de problemas: Abrir as portas necessárias no Windows Server

Na maioria das configurações, as portas necessárias são abertas pela instalação do ASP.NET e o depurador remoto. No entanto, se você estiver solucionando problemas de implantação e o aplicativo é hospedado por trás de um firewall, você precisará verificar se as portas corretas estão abertas.

Em uma VM do Azure, você deve abrir portas por meio de [grupo de segurança de rede](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Portas necessárias:

- 80 - exigido para o IIS
- 4022 - exigido para depuração remota do Visual Studio de 2017 (consulte [as atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md) para obter mais informações).
- UDP 3702 - porta de descoberta (opcional) permite que você o **localizar** botão ao anexar o depurador remoto no Visual Studio.

Além disso, essas portas já devem ser abertas pela instalação do ASP.NET:
- 8172 - (opcional) é necessário para a implantação da Web para implantar o aplicativo do Visual Studio

