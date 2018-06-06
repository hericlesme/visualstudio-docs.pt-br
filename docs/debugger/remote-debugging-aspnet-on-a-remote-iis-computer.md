---
title: Remoto depurar ASP.NET Core em um computador remoto IIS | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 607f4bb2bcce3d8895a4a07df8d70c866e7a6aab
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746924"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio-2017"></a>Depuração remota ASP.NET Core em um computador IIS remoto no Visual Studio de 2017
Para depurar um aplicativo ASP.NET que tenha sido implantado no IIS, instalar e executar as ferramentas remotas no computador onde você implantou seu aplicativo e, em seguida, anexe ao seu aplicativo em execução do Visual Studio.

![Componentes do depurador remoto](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Este guia explica como configurar e configurar um Visual Studio 2017 ASP.NET Core, implantá-lo no IIS e anexar o depurador remoto do Visual Studio. A depuração remota ASP.NET 4.5.2, consulte [ASP.NET de depuração remota em um computador com IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Você também pode implantar e depurar no IIS usando o Azure. Para o serviço de aplicativo do Azure, você pode facilmente implantar e depurar em uma instância pré-configurado do IIS e o depurador remoto usando o [instantâneo depurador](../debugger/debug-live-azure-applications.md) ou [anexar o depurador do Gerenciador de servidores](../debugger/remote-debugging-azure.md).

Esses procedimentos foram testados nessas configurações de servidor:
* Windows Server 2012 R2 e IIS 8
* Windows Server 2016 e IIS 10

## <a name="requirements"></a>Requisitos

Não há suporte para a depuração entre dois computadores conectados por meio de um proxy. Depuração em uma conexão de baixa largura de banda, como dial-up da Internet, ou de alta latência, ou pela Internet entre países não é recomendado e pode falhar ou ser muito lento. Para obter uma lista completa dos requisitos, consulte [requisitos](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>Aplicativo já em execução no IIS?

Este artigo inclui etapas de configuração de uma configuração básica do IIS no Windows server e implantar o aplicativo do Visual Studio. Essas etapas são incluídas para certificar-se de que o servidor tem necessário componentes instalados, que o aplicativo pode ser executado corretamente e que você está pronto para depuração remota.

* Se seu aplicativo estiver em execução no IIS e você quiser apenas para baixar o depurador remoto e iniciar a depuração, vá para [baixar e instalar as ferramentas remotas no Windows Server](#BKMK_msvsmon).

* Se você deseja obter ajuda para certificar-se de que seu aplicativo é configurado, implantado e em execução no IIS para que você pode depurar, siga todas as etapas neste tópico.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Criar o aplicativo do ASP.NET Core no computador Visual Studio de 2017 

1. Crie um novo aplicativo ASP.NET Core. (**Arquivo > Novo > projeto**, em seguida, selecione **Visual C# > Web > aplicativo Web do ASP.NET Core**).

    No **ASP.NET Core** seção de modelos, selecione **aplicativo Web**.

2. Verifique se **ASP.NET Core 2.0** for selecionada, que **Habilitar suporte de Docker** é **não** selecionado e que **autenticação** é definido como **Nenhuma autenticação**.

3. Nomeie o projeto **MyASPApp** e clique em **Okey** para criar a nova solução.

4. Abra o arquivo About.cshtml.cs e definir um ponto de interrupção no `OnGet` método (em modelos mais antigos, abra o HomeController em vez disso e defina o ponto de interrupção `About()` método).

## <a name="bkmk_configureIIS"></a> Instalar e configurar o IIS no Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Atualizar configurações de segurança do navegador no Windows Server

Se a configuração de segurança aprimorada estiver habilitada no Internet Explorer (ela é habilitada por padrão), talvez seja necessário adicionar alguns domínios como sites confiáveis para que você possa baixar alguns dos componentes do servidor web. Adicionar os sites confiáveis, vá para **opções da Internet > Segurança > Sites confiáveis > Sites**. Adicione os domínios a seguir.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Quando você baixar o software, você pode receber solicitações para conceder a permissão para carregar vários scripts do site da web e recursos. Alguns desses recursos não são necessários, mas para simplificar o processo, clique em **adicionar** quando solicitado.

## <a name="install-aspnet-core-on-windows-server"></a>Instalar o ASP.NET Core no Windows Server

1. Instalar o [hospedagem do .NET Core Windows Server](https://aka.ms/dotnetcore-2-windowshosting) pacote no sistema de hospedagem. O pacote instala o .NET Core Runtime, biblioteca principal do .NET e o módulo do ASP.NET Core. Para obter mais instruções detalhadas, consulte [publicar no IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

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

1. Abra o Windows Explorer e crie uma nova pasta, **C:\Publish**, onde você irá implantar posteriormente o projeto ASP.NET.

2. Se ainda não estiver aberto, abra o **serviços de informações da Internet (IIS) Manager**. (No painel esquerdo do Gerenciador do servidor, selecione **IIS**. O servidor e selecione **serviços de informações da Internet (IIS) Manager**.)

3. Em **conexões** no painel esquerdo, vá para **Sites**.

4. Selecione o **Default Web Site**, escolha **configurações básicas**e defina o **caminho físico** para **C:\Publish**.

4. Clique com botão direito do **Default Web Site** nó e selecione **Adicionar aplicativo**.

5. Definir o **Alias** campo **MyASPApp**, aceite o padrão do Pool de aplicativos (**DefaultAppPool**) e defina o **caminho físico** para  **C:\Publish**.

6. Em **conexões**, selecione **Pools de aplicativos**. Abra **DefaultAppPool** e defina o campo de pool de aplicativos **sem código gerenciado**.

7. Clique com botão direito do novo site no Gerenciador do IIS, escolha **editar permissões**e certifique-se de que IUSR, IIS_IUSRS ou o usuário configurado para acesso ao aplicativo web é um usuário autorizado com direitos de leitura e execução.

    Se você não vir um desses usuários com acesso, percorrer as etapas para adicionar IUSR como um usuário com direitos de leitura e execução.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Publicar e implantar o aplicativo pela publicação em uma pasta local do Visual Studio

Você também pode publicar e implantar o aplicativo usando o sistema de arquivos ou outras ferramentas.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a> Baixe e instale as ferramentas remotas no Windows Server

Neste tutorial, estamos usando o Visual Studio de 2017.

Se você tiver dificuldade para abrir a página com o download do depurador remoto, consulte [desbloquear o download do arquivo](../debugger/remote-debugging.md#unblock_msvsmon) para obter ajuda.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> Em alguns cenários, pode ser mais eficiente para executar o depurador remoto de um compartilhamento de arquivos. Para obter mais informações, consulte [executar o depurador remoto de um compartilhamento de arquivo](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a> Configurar o depurador remoto no Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Se você precisa adicionar permissões para usuários adicionais, alterar o modo de autenticação ou número da porta para o depurador remoto, consulte [configurar o depurador remoto](../debugger/remote-debugging.md#configure_msvsmon).

Para obter informações sobre como executar o depurador remoto como um serviço, consulte [executar o depurador remoto como um serviço](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a> Anexar ao aplicativo ASP.NET de computador do Visual Studio

1. No computador do Visual Studio, abra a solução que você está tentando depurar (**MyASPApp** se você estiver seguindo todas as etapas neste artigo).
2. No Visual Studio, clique em **Depurar > Anexar ao processo** (Ctrl + Alt + P).

    > [!TIP]
    > No Visual Studio de 2017, você pode anexar novamente o mesmo processo anteriormente associados a por meio **Depurar > anexe ao processo...** (Shift + Alt + P). 

3. Defina o campo do qualificador  **\<nome do computador remoto >: 4022**.
4. Clique em **atualizar**.
    Você deve ver alguns processos que aparecem no **processos disponíveis** janela.

    Se você não vir todos os processos, tente usar o endereço IP em vez do nome do computador remoto (a porta é necessária). Você pode usar `ipconfig` em uma linha de comando para obter o endereço IPv4.

    Se você quiser usar o **localizar** botão, talvez você precise [abra a porta UDP 3702](#bkmk_openports) no servidor.

5. Verificar **Mostrar processos de todos os usuários**.
6. Digite a primeira letra de um nome de processo para localizar rapidamente **dotnet.exe** (para ASP.NET Core).

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Clique em **Anexar**.

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
- 4022 - exigido para depuração remota do Visual Studio de 2017 (consulte [as atribuições de porta do depurador remoto](../debugger/remote-debugger-port-assignments.md) para obter informações detalhadas.
- 8172 - (opcional) é necessário para a implantação da Web para implantar o aplicativo do Visual Studio.
- UDP 3702 - porta de descoberta (opcional) permite que você o **localizar** botão ao anexar o depurador remoto no Visual Studio.

1. Para abrir uma porta no Windows Server, abra o **iniciar** menu, procure **Firewall do Windows com segurança avançada**.

2. Em seguida, escolha **regras de entrada > nova regra > porta**e, em seguida, clique em **próximo**. (Para UDP 3702, escolha **as regras de saída** em vez disso.)

3. Em **portas locais específicas**, digite o número da porta, clique em **próximo**.

4. Clique em **permitir a Conexão**, clique em **próximo**.

5. Selecione um ou mais tipos de rede para habilitar a porta e clique em **próximo**.

    O tipo que você selecionar deve incluir a rede à qual o computador remoto está conectado.
6. Adicione o nome (por exemplo, **IIS**, **implantação da Web**, ou **msvsmon**) para a regra de entrada e clique em **concluir**.

    Você deve ver a nova regra na lista de regras de entrada ou saída.

    Se você quiser obter mais detalhes sobre como configurar o Firewall do Windows, consulte [configurar o Firewall do Windows para depuração remota](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Crie regras adicionais para as outras portas necessárias.
