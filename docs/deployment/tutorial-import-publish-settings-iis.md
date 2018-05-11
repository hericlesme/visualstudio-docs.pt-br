---
title: Publicar no IIS, importando as configurações de publicação
ms.custom: Create and import a publishing profile to deploy an application from Visual Studio to IIS
ms.date: 05/07/2018
ms.technology: vs-ide-deployment
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1db8ca68453cff105f2bbefcd384b8afa9efea9d
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Publicar um aplicativo no IIS, importando as configurações de publicação no Visual Studio

Você pode usar o **publicar** ferramenta para importar configurações de publicação e, em seguida, implante seu aplicativo. Neste artigo, podemos usar configurações de publicação para o IIS, mas você pode usar etapas semelhantes para importar configurações de publicação para [do serviço de aplicativo do Azure](../deployment/tutorial-import-publish-settings-azure.md). Em alguns cenários, o uso de uma publicação de perfil de configurações pode ser mais rápido do que a configuração manual de implantação para o IIS para cada instalação do Visual Studio.

Estas etapas se aplicam a aplicativos ASP.NET, o ASP.NET Core e o núcleo do .NET no Visual Studio. As etapas correspondem ao Visual Studio 2017 versão 15.6.

Neste tutorial, você irá:

> [!div class="checklist"]
> * Configurar o IIS para que você possa gerar um arquivo de configurações de publicação
> * Criar um arquivo de configurações de publicação
> * Importar o arquivo de configurações de publicação no Visual Studio
> * Implantar o aplicativo para IIS

Um arquivo de configurações de publicação (\*. publishsettings) é diferente de um perfil de publicação (\*. pubxml) criado no Visual Studio. Um arquivo de configurações de publicação é criado pelo IIS ou o serviço de aplicativo do Azure, ou pode ser criado manualmente e, em seguida, ele pode ser importado para o Visual Studio.

> [!NOTE]
> Se você só precisa copiar um perfil de publicação do Visual Studio (\*arquivo. pubxml) de uma instalação do Visual Studio para outro, você pode encontrar o perfil de publicação,  *\<profilename\>. pubxml*, no  *\\< projectname\>\Properties\PublishProfiles* pasta para os tipos de projeto gerenciado. Para sites, procure o *\App_Data* pasta. Os perfis de publicação são arquivos XML do MSBuild.

## <a name="prerequisites"></a>Pré-requisitos

* Você deve ter instalado o Visual Studio e o **ASP.NET** e **do .NET Framework** cargas de trabalho de desenvolvimento. Para um aplicativo .NET Core, você também precisa de **.NET Core** carga de trabalho.

    Se você ainda não instalou o Visual Studio, clique [aqui](http://www.visualstudio.com) para instalá-lo gratuitamente.

    As etapas neste artigo são baseadas no Visual Studio de 2017

* Para gerar o arquivo de configurações de publicação do IIS, você deve ter outro computador executando o Windows Server 2012 com a função de servidor Web do IIS 8.0 configurado corretamente e o ASP.NET 4.5 ou ASP.NET Core instalado. Para o ASP.NET Core, consulte [publicar no IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). Para o ASP.NET 4.5, consulte [IIS 8.0 usando ASP.NET 3.5 e o ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Criar um novo projeto ASP.NET no Visual Studio

1. No computador executando o Visual Studio, escolha **arquivo > Novo projeto**.

1. Em **Visual C#** ou **Visual Basic**, escolha **Web**e, em seguida, no painel central, escolha um **o aplicativo Web do ASP.NET (.NET Framework)** ou (c# somente) **aplicativo Web do ASP.NET Core**e, em seguida, clique em **Okey**.

    Se você não vir os modelos de projeto especificado, clique no **abrir instalador do Visual Studio** link no painel esquerdo do **novo projeto** caixa de diálogo. O Instalador do Visual Studio é iniciado. Consulte os pré-requisitos deste artigo para identificar as cargas de trabalho de Visual Studio necessárias, que deve ser instalado.

1. Escolha **MVC** (.NET Framework) ou **aplicativo Web (Model-View-Controller)** (para .NET Core) e certifique-se de que **sem autenticação** está selecionado e, em seguida, clique em **Okey**.

1. Digite um nome como **MyWebApp** e clique em **Okey**.

    O Visual Studio cria o projeto.

1. Escolha **Construir > Compilar solução** para compilar o projeto.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Instalar e configurar a implantação da Web no Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Criar o arquivo de configurações de publicação no IIS no Windows Server

1. No IIS, clique com botão direito do **Default Web Site**, escolha **implantar** > **configurar Web implantar publicação**.

    ![Definir a configuração de implantação da Web](../deployment/media/tutorial-configure-web-deploy-publishing.png)

1. No **configurar Web implantar publicação** caixa de diálogo caixa, examine as configurações.

1. Clique em **instalação**.

    No **resultados** painel, a saída mostra que os direitos de acesso foi concedida ao usuário especificado e que um arquivo com um *. publishsettings* foi gerada no local mostrado na extensão de arquivo a caixa de diálogo.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    Dependendo da configuração do Windows Server e o IIS, você verá valores diferentes. Aqui estão alguns detalhes sobre os valores que você verá:

    * O *msdeploy.axd* arquivo referenciado no `publishUrl` atributo é um arquivo de manipulador HTTP geradas dinamicamente para implantação da Web. (Para fins de teste, `http://myhostname:8172` geralmente funcionam bem.)
    * O `publishUrl` porta geralmente é definida como porta 8172, que é o padrão para a implantação da Web.
    * O `destinationAppUrl` porta geralmente é definida para a porta 80, que é o padrão para o IIS.
    * Se não for possível conectar-se ao host remoto no Visual Studio usando o nome do host (em etapas posteriores), teste o endereço IP no lugar do nome de host.

    > [!NOTE]
    > Se você estiver publicando para o IIS em execução em uma VM do Azure, as portas do IIS e a implantação da Web devem ser abertas no grupo de segurança de rede. Para obter informações detalhadas, consulte [instalar e executar o IIS](/azure/virtual-machines/windows/quick-create-portal#open-port-80-for-web-traffic).

1. Copie esse arquivo para o computador onde você está executando o Visual Studio.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar as configurações de publicação no Visual Studio e implantar

1. No computador em que o projeto ASP.NET aberto no Visual Studio, clique com botão direito no projeto no Gerenciador de soluções e escolha **publicar**.

1. Se você tiver configurado anteriormente quaisquer perfis de publicação, o **publicar** painel é exibido. Clique em **criar novo perfil**.

1. No **escolher um destino de publicação** caixa de diálogo, clique em **importar perfil**.

    ![Escolher publicar](../deployment/media/tutorial-publish-tool-import-profile.png)

1. Navegue até o local do arquivo de configurações de publicação que você criou na seção anterior.

1. No **importar o arquivo de configurações de publicação** caixa de diálogo, navegue até e selecione o perfil que você criou na seção anterior e clique em **abrir**.

    O Visual Studio inicia o processo de implantação e a janela de saída mostra o progresso e os resultados.

    Se você obtiver uma implantação de quaisquer erros, clique em **configurações** para editar as configurações. Modificar as configurações e clique em **validar** para testar as novas configurações.

    ![Editar as configurações na ferramenta de publicação](../deployment/media/tutorial-configure-publish-settings-in-tool.png)

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, criado um arquivo de configurações de publicação, importe-o para o Visual Studio e implantado um aplicativo ASP.NET no IIS.

> [!div class="nextstepaction"]
> [Introdução à implantação](../deployment/deploying-applications-services-and-components.md)
