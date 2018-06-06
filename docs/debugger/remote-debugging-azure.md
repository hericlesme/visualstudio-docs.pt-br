---
title: Remoto depurar Core de ASP.NET no IIS e o Azure | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/21/2018
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
ms.openlocfilehash: a4e03f9a369959a5736d7030a1dac885771d7984
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746761"
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

    Se você tiver configurado anteriormente quaisquer perfis de publicação, o **publicar** painel é exibido. Clique em **novo perfil**.

1. Escolha **do serviço de aplicativo do Azure** do **publicar** caixa de diálogo, selecione **criar novo**e siga os prompts para publicar.

    Para obter instruções detalhadas, consulte [implantar um aplicativo web do ASP.NET Core para o Azure usando o Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Publicar no Serviço de Aplicativo do Azure](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Abra **Server Explorer** (**exibição** > **Server Explorer**), com o botão direito na instância do serviço de aplicativo e escolha **Anexar depurador**.

1. No aplicativo ASP.NET em execução, clique no link para o **sobre** página.

    O ponto de interrupção deve ser atingido no Visual Studio.

    É só isso! O restante das etapas neste tópico se aplicam a depuração remota em uma VM do Azure.

## <a name="remote_debug_azure_vm"></a> Depuração remota ASP.NET Core em uma VM do Azure

Você pode criar uma VM do Azure para o Windows Server e, em seguida, instalar e configurar o IIS e outros componentes de software necessárias. Isso leva mais tempo que a implantação para um serviço de aplicativo do Azure e requer que você siga as etapas restantes neste tutorial.

Primeiro, siga todas as etapas descritas em [instalar e executar o IIS](/azure/virtual-machines/windows/quick-create-portal).

Quando você abre a porta 80 no grupo de segurança de rede, também abra a porta 4022 para o depurador remoto. Dessa forma, você não precisará abri-lo mais tarde.

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Aplicativo já em execução no IIS na VM do Azure?

Este artigo inclui etapas de configuração de uma configuração básica do IIS no Windows server e implantar o aplicativo do Visual Studio. Essas etapas são incluídas para certificar-se de que o servidor tem os componentes necessários instalados, que o aplicativo pode ser executado corretamente e que você está pronto para depuração remota.

* Se seu aplicativo estiver em execução no IIS e você quiser apenas para baixar o depurador remoto e iniciar a depuração, vá para [baixar e instalar as ferramentas remotas no Windows Server](#BKMK_msvsmon).

* Se você deseja obter ajuda para certificar-se de que seu aplicativo é configurado, implantado e em execução no IIS para que você pode depurar, siga todas as etapas neste tópico.

### <a name="update-browser-security-settings-on-windows-server"></a>Atualizar configurações de segurança do navegador no Windows Server

Se a configuração de segurança aprimorada estiver habilitada no Internet Explorer (ela é habilitada por padrão), talvez seja necessário adicionar alguns domínios como sites confiáveis para que você possa baixar alguns dos componentes do servidor web. Adicionar os sites confiáveis, vá para **opções da Internet > Segurança > Sites confiáveis > Sites**. Adicione os domínios a seguir.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Quando você baixar o software, você pode receber solicitações para conceder a permissão para carregar vários scripts do site da web e recursos. Alguns desses recursos não são necessários, mas para simplificar o processo, clique em **adicionar** quando solicitado.

### <a name="install-aspnet-core-on-windows-server"></a>Instalar o ASP.NET Core no Windows Server

1. Instalar o [hospedagem do .NET Core Windows Server](https://aka.ms/dotnetcore-2-windowshosting) pacote no sistema de hospedagem. O pacote instalará o .NET Core Runtime, biblioteca principal do .NET e o módulo do ASP.NET Core. Para obter mais instruções detalhadas, consulte [publicar no IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Se o sistema não tiver uma conexão de Internet, obtenha e instale o *[Microsoft Visual C++ 2015 redistribuível](https://www.microsoft.com/download/details.aspx?id=53840)* antes de instalar o pacote de hospedagem do .NET Core Windows Server.

3. Reiniciar o sistema (ou execute **net stop foi /y** seguido por **net start-w3svc** em um prompt de comando para acompanhar uma alteração no caminho do sistema).

## <a name="choose-a-deployment-option"></a>Escolha uma opção de implantação

Se você precisar de ajuda para implantar o aplicativo ao IIS, considere estas opções:

* Implante criando um arquivo de configurações de publicação no IIS e importar as configurações no Visual Studio. Em alguns cenários, isso é uma maneira rápida de implantar seu aplicativo. Quando você cria o arquivo de configurações de publicação, permissões são automaticamente definidas no IIS.

* Implante, publicando em uma pasta local e copiar a saída por um método preferencial para uma pasta de aplicativo preparada no IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Opcional) Implantar usando um arquivo de configurações de publicação

Você pode usar essa opção cria um arquivo de configurações de publicação e importá-lo no Visual Studio.

> [!NOTE]
> Esse método de implantação usa a implantação da Web. Se você quiser configurar a implantação da Web manualmente no Visual Studio em vez de importar as configurações, você pode instalar o Web implantar 3.6 em vez de Web implantar 3.6 para servidores de hospedagem. No entanto, se você configurar a implantação da Web manualmente, você precisará certificar-se de que uma pasta de aplicativo no servidor é configurada com os valores corretos e as permissões (consulte [configurar o site do ASP.NET](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Instalar e configurar a implantação da Web para servidores de hospedagem no Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Criar o arquivo de configurações de publicação no IIS no Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar as configurações de publicação no Visual Studio e implantar

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Depois que o aplicativo implanta com êxito, ele deve ser iniciado automaticamente. Se o aplicativo não for iniciado no Visual Studio, inicie o aplicativo no IIS. Para o ASP.NET Core, você precisa certificar-se de que o pool de aplicativos campo para o **DefaultAppPool** é definido como **sem código gerenciado**.

1. No **configurações** caixa de diálogo, habilite a depuração clicando **próximo**, escolha um **depurar** configuração e, em seguida, escolha **remover arquivos adicionais no destino** sob o **Publicar arquivo** opções.

    > [!NOTE]
    > Se você escolher uma configuração de versão, você desabilitar a depuração no *Web. config* arquivo quando você publicar.

1. Clique em **salvar** e, em seguida, republicar o aplicativo.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Opcional) Implantar pela publicação em uma pasta local

Você pode usar essa opção para implantar seu aplicativo, se você deseja copiar o aplicativo ao IIS usando o Powershell, RoboCopy, ou se você deseja copiar os arquivos manualmente.

### <a name="BKMK_deploy_asp_net"></a> Configurar o site da Web do ASP.NET no computador Windows Server

Se você estiver importando as configurações de publicação, você poderá ignorar esta seção.

1. Abra o **serviços de informações da Internet (IIS) Manager** e vá para **Sites**.

2. Clique com botão direito do **Default Web Site** nó e selecione **Adicionar aplicativo**.

3. Definir o **Alias** campo **MyASPApp** e o campo de pool de aplicativos para **sem código gerenciado**. Definir o **caminho físico** para **C:\Publish** (onde você irá implantar posteriormente o projeto ASP.NET).

4. Com o site selecionado no Gerenciador do IIS, escolha **editar permissões**e certifique-se de que IUSR, IIS_IUSRS ou o usuário configurado para o Pool de aplicativos é um usuário autorizado com direitos de leitura e execução.

    Se você não vir um desses usuários com acesso, percorrer as etapas para adicionar IUSR como um usuário com direitos de leitura e execução.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Opcional) Publicar e implantar o aplicativo pela publicação em uma pasta local do Visual Studio

Se você não estiver usando a implantação da Web, você deve publicar e implantar o aplicativo usando o sistema de arquivos ou outras ferramentas. Você pode começar criando um pacote usando o sistema de arquivos e, em seguida, implantar o pacote manualmente ou usar outras ferramentas, como XCopy, RoboCopy ou PowerShell. Nesta seção, vamos supor que são copiar manualmente o pacote, se você não estiver usando a implantação da Web.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a> Baixe e instale as ferramentas remotas no Windows Server

Neste tutorial, estamos usando o Visual Studio de 2017.

Se você tiver dificuldade para abrir a página com o download do depurador remoto, consulte [desbloquear o download do arquivo](../debugger/remote-debugging.md#unblock_msvsmon) para obter ajuda.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Configurar o depurador remoto no Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se você precisa adicionar permissões para usuários adicionais, alterar o modo de autenticação ou número da porta para o depurador remoto, consulte [configurar o depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a> Anexar ao aplicativo ASP.NET de computador do Visual Studio

1. No computador do Visual Studio, abra a solução que você está tentando depurar (**MyASPApp** se você estiver seguindo as etapas neste artigo).
2. No Visual Studio, clique em **Depurar > Anexar ao processo** (Ctrl + Alt + P).

    > [!TIP]
    > No Visual Studio de 2017, você pode anexar novamente para o mesmo processo anteriormente conectados a usando **Depurar > anexe ao processo...** (Shift + Alt + P). 

3. Defina o campo do qualificador  **\<nome do computador remoto >: 4022**.
4. Clique em **atualizar**.
    Você deve ver alguns processos que aparecem no **processos disponíveis** janela.

    Se você não vir todos os processos, tente usar o endereço IP em vez do nome do computador remoto (a porta é necessária). Você pode usar `ipconfig` em uma linha de comando para obter o endereço IPv4.

    Se você quiser usar o **localizar** botão, talvez você precise [abra a porta UDP 3702](#bkmk_openports) no servidor.

5. Verificar **Mostrar processos de todos os usuários**.

6. Digite a primeira letra de um nome de processo para localizar rapidamente *dotnet.exe* (para ASP.NET Core).
   
   Para um aplicativo ASP.NET Core, o nome do processo anterior foi *dnx.exe*.

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

