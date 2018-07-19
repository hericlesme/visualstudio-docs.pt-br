---
title: Implantar o ASP.NET no IIS usando a implantação da Web
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
ms.openlocfilehash: 4705ca6e72001f8930e2fa4270515df53e1213a8
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080844"
---
# <a name="deploy-aspnet-to-a-remote-iis-computer-using-web-deploy-in-visual-studio"></a>Implantar o ASP.NET a um computador remoto do IIS usando a implantação da Web no Visual Studio

Este artigo explica como configurar e configurar um aplicativo do Visual Studio 2017 ASP.NET MVC 4.5.2 e implantá-lo no IIS. Este artigo inclui etapas sobre como configurar uma configuração básica do IIS no Windows server e implantar o aplicativo do Visual Studio. Essas etapas são incluídas para certificar-se de que o servidor tem necessário componentes instalados e que você está pronto para implantar. Se você estiver implantando um aplicativo ASP.NET Core, algumas etapas são diferentes. Para implantar um aplicativo ASP.NET Core, consulte [publicar um aplicativo no IIS, importando as configurações de publicação](../deployment/tutorial-import-publish-settings-iis.md) para obter instruções. Em alguns cenários ASP.NET e ASP.NET Core, é mais rápido implantar no IIS, importando as configurações de publicação.

Esses procedimentos foram testados nessas configurações de servidor:
* Windows Server 2012 R2 e IIS 8 (para o Windows Server 2008 R2, as etapas do servidor são diferentes)

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Criar do ASP.NET 4.5.2 aplicativo no computador do Visual Studio
  
1. No computador executando o Visual Studio, escolha **arquivo** > **novo projeto**.

1. Sob **Visual c#** ou **Visual Basic**, escolha **Web**e, em seguida, no painel central, escolha o **aplicativo Web ASP.NET (.NET Framework)** e, em seguida, clique em **Okey**.

    Clique se você não vir os modelos de projeto especificado, o **abrir instalador do Visual Studio** link no painel esquerdo do **novo projeto** caixa de diálogo. O Instalador do Visual Studio é iniciado. Consulte os pré-requisitos deste artigo para identificar as cargas de trabalho de Visual Studio necessárias, que deve ser instalado.

1. Escolher **MVC** (.NET Framework) e certifique-se de que **sem autenticação** está selecionado e, em seguida, clique em **Okey**.

1. Digite um nome como **MyWebApp** e clique em **Okey**.

    O Visual Studio cria o projeto.

1. Escolher **construir** > **compilar solução** para compilar o projeto.

## <a name="install-and-configure-iis-on-windows-server"></a>Instalar e configurar o IIS no Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Atualizar configurações de segurança do navegador no Windows Server

Se a configuração de segurança aprimorada estiver habilitada no Internet Explorer (ela é habilitada por padrão), em seguida, você precisa adicionar alguns domínios como sites confiáveis para que você possa baixar alguns dos componentes do servidor web. Adicione os sites confiáveis acessando **opções da Internet** > **segurança** > **Sites confiáveis** > **Sites** . Adicione os domínios a seguir.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Quando você baixar o software, você pode receber solicitações para conceder permissão para carregar vários scripts do site da web e recursos. Alguns desses recursos não são necessárias, mas para simplificar o processo, clique em **adicionar** quando solicitado.

## <a name="install-aspnet-45-on-windows-server"></a>Instalar o ASP.NET 4.5 no Windows Server

Se você quiser obter informações mais detalhadas para instalar o ASP.NET no IIS, consulte [IIS 8.0 usando ASP.NET 3.5 e ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. No painel esquerdo do Gerenciador do servidor, selecione **IIS**. O servidor com o botão direito e selecione **serviços de informações da Internet (IIS) Manager**.

1. Use o Web Platform Installer (WebPI) para instalar o ASP.NET 4.5 (no nó do servidor no Windows Server 2012 R2, escolha **obter novos componentes do Web Platform** e, em seguida, pesquise por ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Se você estiver usando o Windows Server 2008 R2, instale o ASP.NET 4, em vez de usar este comando:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Reinicie o sistema (ou execute **net stop was /y** seguido **net start w3svc-** em um prompt de comando para acompanhar uma alteração no caminho do sistema).

## <a name="install-web-deploy-36-on-windows-server"></a>Install Web implantar 3.6 no Windows Server

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="configure-aspnet-web-site-on-the-windows-server-computer"></a>Configurar o site da Web ASP.NET no computador com Windows Server

1. Abra o Windows Explorer e crie uma nova pasta, **C:\Publish**, onde você irá implantar posteriormente o projeto do ASP.NET.

2. Se não ainda estiver aberto, abra o **serviços de informações da Internet (IIS) Manager**. (No painel esquerdo do Gerenciador do servidor, selecione **IIS**. O servidor com o botão direito e selecione **serviços de informações da Internet (IIS) Manager**.)

3. Sob **conexões** no painel esquerdo, vá até **Sites**.

4. Selecione o **Site padrão**, escolha **configurações básicas**e defina o **caminho físico** para **C:\Publish**.

5. Clique com botão direito do **Site padrão** nó e selecione **Adicionar aplicativo**.

6. Defina a **Alias** campo **MyASPApp**, aceite o padrão do Pool de aplicativos (**DefaultAppPool**) e defina o **caminho físico** para  **C:\Publish**.

7. Sob **conexões**, selecione **Pools de aplicativos**. Abra **DefaultAppPool** e defina o campo de pool de aplicativos como **ASP.NET v4.0** (ASP.NET 4.5 não é uma opção para o pool de aplicativos).

8. Com o site selecionado no Gerenciador do IIS, escolha **editar permissões**e certifique-se de que IUSR, IIS_IUSRS ou o usuário configurado para o Pool de aplicativos é um usuário autorizado com direitos de leitura e execução. Se nenhum desses usuários estiver presente, adicione IUSR como um usuário com direitos de leitura e execução.

## <a name="publish-and-deploy-the-app-using-web-deploy-from-visual-studio"></a>Publicar e implantar o aplicativo usando a implantação da Web do Visual Studio

[!INCLUDE [deploy-app-web-deploy](../deployment/includes/deploy-app-web-deploy.md)]

Além disso, você talvez precise ler a seção a seguir sobre como solucionar problemas de portas.

## <a name="troubleshoot-open-required-ports-on-windows-server"></a>Solução de problemas: Abrir as portas necessárias no Windows Server

Na maioria das configurações, as portas necessárias estão abertas pela instalação do ASP.NET e a implantação da Web. No entanto, talvez você precise verificar se as portas estão abertas.

> [!NOTE]
> Em uma VM do Azure, você deve abrir as portas por meio de [grupo de segurança de rede](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Portas necessárias:

* 80 - obrigatórias para IIS
* 8172 - necessários para a implantação da Web para implantar o aplicativo do Visual Studio

1. Para abrir uma porta no Windows Server, abra o **inicie** menu, procure **Firewall do Windows com segurança avançada**.

2. Em seguida, escolha **regras de entrada** > **nova regra** > **porta**. Escolher **próxima** e, em **portas locais específicas**, insira o número da porta, clique em **próxima**, em seguida, **permitir a Conexão**, clique em Avançar, e Adicione o nome (**IIS**, **implantação da Web**, ou **msvsmon**) para a regra de entrada.

    Se você quiser obter mais detalhes sobre como configurar o Firewall do Windows, consulte [configurar o Firewall do Windows para depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Crie regras adicionais para as outras portas necessárias.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você criou um arquivo de configurações de publicação, importou para o Visual Studio e implantado um aplicativo ASP.NET no IIS. Você também pode implantar, importando as configurações de publicação.

> [!div class="nextstepaction"]
> [Implantar no IIS, importando as configurações de publicação](../deployment/tutorial-import-publish-settings-iis.md)
