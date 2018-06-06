---
title: Implantar o ASP.NET em IIS usando a implantação da Web
ms.custom: ''
ms.date: 06/04/2018
ms.technology: vs-ide-deployment
ms.topic: tutorial
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: a63d9947f544ddff1de81aaf34ed62c9646fba3d
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34794184"
---
# <a name="deploy-aspnet-to-a-remote-iis-computer-using-web-deploy-in-visual-studio"></a>Implantar o ASP.NET em um computador remoto do IIS usando a implantação da Web no Visual Studio

Este artigo explica como configurar e configurar um aplicativo do Visual Studio 2017 ASP.NET MVC 4.5.2 e implantá-lo no IIS. Este artigo inclui etapas de configuração de uma configuração básica do IIS no Windows server e implantar o aplicativo do Visual Studio. Essas etapas são incluídas para certificar-se de que o servidor tem necessário componentes instalados e que você está pronto para implantar. Se você estiver implantando um aplicativo do ASP.NET Core, algumas etapas são diferentes. Para implantar um aplicativo ASP.NET Core, consulte [publicar um aplicativo IIS importando as configurações de publicação](../deployment/tutorial-import-publish-settings-iis.md) para obter instruções. Em alguns cenários ASP.NET e ASP.NET Core, é mais rápido implantar configurações de publicação do IIS com a importação.

Esses procedimentos foram testados nessas configurações de servidor:
* Windows Server 2012 R2 e IIS 8 (para o Windows Server 2008 R2, as etapas do servidor são diferentes)

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Criar o ASP.NET 4.5.2 aplicativo no computador do Visual Studio
  
1. No computador executando o Visual Studio, escolha **arquivo > Novo projeto**.

1. Em **Visual C#** ou **Visual Basic**, escolha **Web**e, em seguida, no painel central, escolha um **o aplicativo Web do ASP.NET (.NET Framework)** e, em seguida, clique em **Okey**.

    Se você não vir os modelos de projeto especificado, clique no **abrir instalador do Visual Studio** link no painel esquerdo do **novo projeto** caixa de diálogo. O Instalador do Visual Studio é iniciado. Consulte os pré-requisitos deste artigo para identificar as cargas de trabalho de Visual Studio necessárias, que deve ser instalado.

1. Escolha **MVC** (.NET Framework) e certifique-se de que **sem autenticação** está selecionado e, em seguida, clique em **Okey**.

1. Digite um nome como **MyWebApp** e clique em **Okey**.

    O Visual Studio cria o projeto.

1. Escolha **Construir > Compilar solução** para compilar o projeto.

## <a name="bkmk_configureIIS"></a> Instalar e configurar o IIS no Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Atualizar configurações de segurança do navegador no Windows Server

Se a configuração de segurança aprimorada estiver habilitada no Internet Explorer (ela é habilitada por padrão), talvez seja necessário adicionar alguns domínios como sites confiáveis para que você possa baixar alguns dos componentes do servidor web. Adicionar os sites confiáveis, vá para **opções da Internet > Segurança > Sites confiáveis > Sites**. Adicione os domínios a seguir.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Quando você baixar o software, você pode receber solicitações para conceder a permissão para carregar vários scripts do site da web e recursos. Alguns desses recursos não são necessários, mas para simplificar o processo, clique em **adicionar** quando solicitado.

## <a name="BKMK_deploy_asp_net"></a> Instalar o ASP.NET 4.5 no Windows Server

Se você quiser obter informações mais detalhadas para instalar o ASP.NET no IIS, consulte [IIS 8.0 usando ASP.NET 3.5 e o ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. No painel esquerdo do Gerenciador do servidor, selecione **IIS**. O servidor e selecione **serviços de informações da Internet (IIS) Manager**.

1. Use o Web Platform Installer (WebPI) para instalar o ASP.NET 4.5 (no nó do servidor no Windows Server 2012 R2, escolha **obter novos componentes do Web Platform** e, em seguida, procure ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Se você estiver usando o Windows Server 2008 R2, instale o ASP.NET 4, em vez de usar este comando:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Reiniciar o sistema (ou execute **net stop foi /y** seguido por **net start-w3svc** em um prompt de comando para acompanhar uma alteração no caminho do sistema).

## <a name="BKMK_install_webdeploy"></a> Instalar Web implantar 3.6 no Windows Server

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="BKMK_deploy_asp_net"></a> Configurar o site da Web ASP.NET no computador Windows Server

1. Abra o Windows Explorer e crie uma nova pasta, **C:\Publish**, onde você irá implantar posteriormente o projeto ASP.NET.

2. Se ainda não estiver aberto, abra o **serviços de informações da Internet (IIS) Manager**. (No painel esquerdo do Gerenciador do servidor, selecione **IIS**. O servidor e selecione **serviços de informações da Internet (IIS) Manager**.)

3. Em **conexões** no painel esquerdo, vá para **Sites**.

4. Selecione o **Default Web Site**, escolha **configurações básicas**e defina o **caminho físico** para **C:\Publish**.

5. Clique com botão direito do **Default Web Site** nó e selecione **Adicionar aplicativo**.

6. Definir o **Alias** campo **MyASPApp**, aceite o padrão do Pool de aplicativos (**DefaultAppPool**) e defina o **caminho físico** para  **C:\Publish**.

7. Em **conexões**, selecione **Pools de aplicativos**. Abra **DefaultAppPool** e defina o campo de pool de aplicativos **ASP.NET v 4.0** (ASP.NET 4.5 não é uma opção para o pool de aplicativos).

8. Com o site selecionado no Gerenciador do IIS, escolha **editar permissões**e certifique-se de que IUSR, IIS_IUSRS ou o usuário configurado para o Pool de aplicativos é um usuário autorizado com direitos de leitura e execução. Se nenhum desses usuários estiver presente, adicione IUSR como um usuário com direitos de leitura e execução.

## <a name="bkmk_webdeploy"></a> Publicar e implantar o aplicativo usando a implantação da Web do Visual Studio

[!INCLUDE [deploy-app-web-deploy](../deployment/includes/deploy-app-web-deploy.md)]

Além disso, talvez seja necessário ler a seção em [portas de solução de problemas](#bkmk_openports).

## <a name="bkmk_openports"></a> Solução de problemas: Abrir as portas necessárias no Windows Server

Na maioria das configurações, as portas necessárias são abertas pela instalação do ASP.NET e a implantação da Web. No entanto, talvez seja necessário verificar se as portas estão abertas.

> [!NOTE]
> Em uma VM do Azure, você deve abrir portas por meio de [grupo de segurança de rede](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Portas necessárias:

* 80 - exigido para o IIS
* 8172 - necessários para a implantação da Web para implantar o aplicativo do Visual Studio

1. Para abrir uma porta no Windows Server, abra o **iniciar** menu, procure **Firewall do Windows com segurança avançada**.

2. Em seguida, escolha **regras de entrada > nova regra > porta**. Escolha **próximo** e, em **portas locais específicas**, digite o número da porta, clique em **próximo**, em seguida, **permitir a Conexão**, clique em Avançar, e Adicione o nome (**IIS**, **implantação da Web**, ou **msvsmon**) para a regra de entrada.

    Se você quiser obter mais detalhes sobre como configurar o Firewall do Windows, consulte [configurar o Firewall do Windows para depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Crie regras adicionais para as outras portas necessárias.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, criado um arquivo de configurações de publicação, importe-o para o Visual Studio e implantado um aplicativo ASP.NET no IIS. Você também pode implantar importando as configurações de publicação.

> [!div class="nextstepaction"]
> [Implantar configurações de publicação do IIS, importando](../deployment/tutorial-import-publish-settings-iis.md)