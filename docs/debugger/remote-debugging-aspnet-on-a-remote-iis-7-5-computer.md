---
title: Remoto depurar ASP.NET em um computador remoto IIS | Microsoft Docs
ms.custom: remotedebugging
ms.date: 07/26/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: ff8408ecdf8036a6ec00bdbc3ec93f4b41a2a7fa
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>Depuração remota ASP.NET em um computador remoto do IIS
Para depurar um aplicativo ASP.NET que tenha sido implantado no IIS, instalar e executar as ferramentas remotas no computador onde você implantou seu aplicativo e, em seguida, anexe ao seu aplicativo em execução do Visual Studio.

![Componentes do depurador remoto](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Este guia explica como configurar e configurar um aplicativo do Visual Studio 2017 ASP.NET MVC 4.5.2, implantá-lo no IIS e anexar o depurador remoto do Visual Studio. A depuração remota ASP.NET Core, consulte [remota de depuração ASP.NET Core em um computador com IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md). Para o serviço de aplicativo do Azure, você pode facilmente implantar e depurar em uma instância pré-configurado do IIS usando o [instantâneo depurador](../debugger/debug-live-azure-applications.md) (.NET 4.6.1 necessário) ou por [anexar o depurador do Gerenciador de servidores](../debugger/remote-debugging-azure.md).

Esses procedimentos foram testados nessas configurações de servidor:
* Windows Server 2012 R2 e IIS 8 (para o Windows Server 2008 R2, as etapas do servidor são diferentes)

## <a name="requirements"></a>Requisitos

O depurador remoto é suportado no Windows Server, iniciando com o Windows Server 2008 Service Pack 2. Para obter uma lista completa dos requisitos, consulte [requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Não há suporte para a depuração entre dois computadores conectados por meio de um proxy. Depuração em uma conexão de baixa largura de banda, como dial-up da Internet, ou de alta latência, ou pela Internet entre países não é recomendado e pode falhar ou ser muito lento.

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Criar o ASP.NET 4.5.2 aplicativo no computador do Visual Studio
  
1. Crie um novo aplicativo ASP.NET MVC. (**Arquivo > Novo > projeto**, em seguida, selecione * * Visual C# > Web > aplicativo Web ASP.NET. No **ASP.NET 4.5.2** seção de modelos, selecione **MVC**. Verifique se **Habilitar suporte de Docker** não está selecionado e que **autenticação** é definido como **sem autenticação**. Nomeie o projeto **MyASPApp**.)

2. Abra o arquivo HomeController e definir um ponto de interrupção no `About()` método.

## <a name="bkmk_configureIIS"></a> Instalar e configurar o IIS no Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Atualizar configurações de segurança do navegador no Windows Server

Dependendo de suas configurações de segurança, isso pode economizar tempo para adicionar os seguintes sites confiáveis no seu navegador para que você pode facilmente baixar o software descrito neste tutorial. Acesso a esses sites pode ser necessários:

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- visualstudio.com

Se você estiver usando o Internet Explorer, você pode adicionar sites confiáveis, vá para **opções da Internet > Segurança > Sites confiáveis > Sites**. Essas etapas são diferentes para outros navegadores. (Se você precisar baixar uma versão mais antiga do depurador remoto do my.visualstudio.com, alguns sites confiáveis adicionais são necessário para entrar.)

Quando você baixar o software, você pode receber solicitações para conceder a permissão para carregar vários scripts do site da web e recursos. Na maioria dos casos, esses recursos adicionais não são necessários para instalar o software.

## <a name="BKMK_deploy_asp_net"></a> Instalar o ASP.NET 4.5 no Windows Server

Se você quiser obter informações mais detalhadas para instalar o ASP.NET no IIS, consulte [IIS 8.0 usando ASP.NET 3.5 e o ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. Use o Web Platform Installer (WebPI) para instalar o ASP.NET 4.5 (no nó do servidor no Windows Server 2012 R2, escolha **obter novos componentes do Web Platform** e, em seguida, procure ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Se você estiver usando o Windows Server 2008 R2, instale o ASP.NET 4, em vez de usar este comando:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Reiniciar o sistema (ou execute **net stop foi /y** seguido por **net start-w3svc** em um prompt de comando para acompanhar uma alteração no caminho do sistema).

## <a name="BKMK_install_webdeploy"></a> (Opcional) Instalar Web implantar 3.6 no Windows Server

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="BKMK_deploy_asp_net"></a> Configurar o site da Web ASP.NET no computador Windows Server

1. Abra o Windows Explorer e crie uma nova pasta, **C:\Publish**, onde você irá implantar posteriormente o projeto ASP.NET.

2. Abra o **serviços de informações da Internet (IIS) Manager**. (No painel esquerdo do Gerenciador do servidor, selecione **IIS**. O servidor e selecione **serviços de informações da Internet (IIS) Manager**.)

3. Em **conexões** no painel esquerdo, vá para **Sites**.

4. Selecione o **Default Web Site**, escolha **configurações básicas**e defina o **caminho físico** para **C:\Publish**.

5. Clique com botão direito do **Default Web Site** nó e selecione **Adicionar aplicativo**.

6. Definir o **Alias** campo **MyASPApp**, aceite o padrão do Pool de aplicativos (**DefaultAppPool**) e defina o **caminho físico** para  **C:\Publish**.

7. Em **conexões**, selecione **Pools de aplicativos**. Abra **DefaultAppPool** e defina o campo de pool de aplicativos **ASP.NET v 4.0** (ASP.NET 4.5 não é uma opção para o pool de aplicativos).

8. Com o site selecionado no Gerenciador do IIS, escolha **editar permissões**e certifique-se de que IUSR, IIS_IUSRS ou o usuário configurado para o Pool de aplicativos é um usuário autorizado com direitos de leitura e execução. Se nenhum desses usuários estiver presente, adicione IUSR como um usuário com direitos de leitura e execução.

## <a name="bkmk_webdeploy"></a> (Opcional) Publicar e implantar o aplicativo usando a implantação da Web do Visual Studio

[!INCLUDE [remote-debugger-deploy-app-web-deploy](../debugger/includes/remote-debugger-deploy-app-web-deploy.md)]

Além disso, talvez seja necessário ler a seção em [portas de solução de problemas](#bkmk_openports).

## <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Opcional) Publicar e implantar o aplicativo pela publicação em uma pasta local do Visual Studio

Você também pode publicar e implantar o aplicativo usando o sistema de arquivos ou outras ferramentas.

1. (ASP.NET 4.5.2) Certifique-se de que o arquivo Web. config lista a versão correta do .NET Framework.  Por exemplo, se você estiver direcionando a ASP.NET 4.5.2, verifique se que essa versão é listada no Web. config.
  
    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>
  
    ```

    Por exemplo, a versão deve ser 4.0, se você instalar o ASP.NET 4, em vez de 4.5.2.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a> Baixe e instale as ferramentas remotas no Windows Server

Neste tutorial, estamos usando o Visual Studio de 2017.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> Em alguns cenários, pode ser mais eficiente para executar o depurador remoto de um compartilhamento de arquivos. Para obter mais informações, consulte [executar o depurador remoto de um compartilhamento de arquivo](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a> Configurar o depurador remoto no Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se você precisa adicionar permissões para usuários adicionais, alterar o modo de autenticação ou número da porta para o depurador remoto, consulte [configurar o depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

Para obter informações sobre como executar o depurador remoto como um serviço, consulte [executar o depurador remoto como um serviço](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a> Anexar ao aplicativo ASP.NET de computador do Visual Studio

1. No computador do Visual Studio, abra o **MyASPApp** solução.
2. No Visual Studio, clique em **Depurar > Anexar ao processo** (Ctrl + Alt + P).

    > [!TIP]
    > No Visual Studio de 2017, você pode anexar novamente o mesmo processo anteriormente associados a por meio **Depurar > anexe ao processo...** (Shift + Alt + P). 

3. Defina o campo do qualificador  **\<nome do computador remoto >: 4022**.
4. Clique em **atualizar**.
    Você deve ver alguns processos que aparecem no **processos disponíveis** janela.

    Se você não vir todos os processos, tente usar o endereço IP em vez do nome do computador remoto (a porta é necessária). Você pode usar `ipconfig` em uma linha de comando para obter o endereço IPv4.

5. Verificar **Mostrar processos de todos os usuários**.
6. Digite a primeira letra de um nome de processo para localizar rapidamente **w3wp.exe** para ASP.NET 4.5.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess.png "RemoteDBG_AttachToProcess")

7. Clique em **anexar**

8. Abra o site do computador remoto. Em um navegador, vá para **http://\<nome do computador remoto >**.
    
    Você verá a página da web ASP.NET.
9. No aplicativo ASP.NET em execução, clique no link para o **sobre** página.

    O ponto de interrupção deve ser atingido no Visual Studio.

## <a name="bkmk_openports"></a> Solução de problemas: Abrir as portas necessárias no Windows Server

Na maioria das configurações, as portas necessárias são abertas pela instalação do ASP.NET e o depurador remoto. No entanto, talvez seja necessário verificar se as portas estão abertas.

> [!NOTE]
> Em uma VM do Azure, você deve abrir portas por meio de [grupo de segurança de rede](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Portas necessárias:

- 80 - exigido para o IIS
- 8172 - (opcional) é necessário para a implantação da Web para implantar o aplicativo do Visual Studio
- 4022 - exigido para depuração remota do Visual Studio de 2017 (consulte [as atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md) para obter informações detalhadas.
- UDP 3702 - porta de descoberta (opcional) permite que você o **localizar** botão ao anexar o depurador remoto no Visual Studio.

1. Para abrir uma porta no Windows Server, abra o **iniciar** menu, procure **Firewall do Windows com segurança avançada**.

2. Em seguida, escolha **regras de entrada > nova regra > porta**. Escolha **próximo** e, em **portas locais específicas**, digite o número da porta, clique em **próximo**, em seguida, **permitir a Conexão**, clique em Avançar, e Adicione o nome (**IIS**, **implantação da Web**, ou **msvsmon**) para a regra de entrada.

    Se você quiser obter mais detalhes sobre como configurar o Firewall do Windows, consulte [configurar o Firewall do Windows para depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Crie regras adicionais para as outras portas necessárias.