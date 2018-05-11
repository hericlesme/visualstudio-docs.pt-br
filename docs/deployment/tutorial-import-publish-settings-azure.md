---
title: Publicar no Azure importando as configurações de publicação
ms.custom: Create and import a publishing profile to deploy an application from Visual Studio to Azure App Service
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
ms.openlocfilehash: a0fcc9f6ec4143a757139a9e013f1a1f4dbe666e
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Publicar um aplicativo para o serviço de aplicativo do Azure importando as configurações de publicação no Visual Studio

Você pode usar o **publicar** ferramenta para importar configurações de publicação e, em seguida, implante seu aplicativo. Neste artigo, podemos usar configurações de publicação para o serviço de aplicativo do Azure, mas você pode usar etapas semelhantes para importar configurações de publicação [IIS](../deployment/tutorial-import-publish-settings-iis.md). Em alguns cenários, o uso de uma publicação de perfil de configurações pode ser mais rápido do que a configuração manual de implantação para o serviço para cada instalação do Visual Studio.

Estas etapas se aplicam a aplicativos ASP.NET, o ASP.NET Core e o núcleo do .NET no Visual Studio. As etapas correspondem ao Visual Studio 2017 versão 15.6.

Neste tutorial, você irá:

> [!div class="checklist"]
> * Gerar um arquivo de configurações de publicação do serviço de aplicativo do Azure
> * Importar o arquivo de configurações de publicação no Visual Studio
> * Implantar o aplicativo do serviço de aplicativo do Azure

Um arquivo de configurações de publicação (*. publishsettings) é diferente de um perfil de publicação (*. pubxml) criado no Visual Studio. Um arquivo de configurações de publicação é criado pelo serviço de aplicativo do Azure e, em seguida, ele pode ser importado para o Visual Studio.

> [!NOTE]
> Se você só precisa copiar um perfil de publicação do Visual Studio (\*arquivo. pubxml) de uma instalação do Visual Studio para outro, você pode encontrar o perfil de publicação,  *\<profilename\>. pubxml*, no  *\\< projectname\>\Properties\PublishProfiles* pasta para os tipos de projeto gerenciado. Para sites, procure o *\App_Data* pasta. Os perfis de publicação são arquivos XML do MSBuild.

## <a name="prerequisites"></a>Pré-requisitos

* Você deve ter instalado o Visual Studio e o **ASP.NET** e **do .NET Framework** cargas de trabalho de desenvolvimento. Para um aplicativo .NET Core, você também precisa de **.NET Core** carga de trabalho.

    Se você ainda não instalou o Visual Studio, clique [aqui](http://www.visualstudio.com) para instalá-lo gratuitamente.

* Crie um serviço de aplicativo do Azure. Para obter instruções detalhadas, consulte [implantar um aplicativo web do ASP.NET Core para o Azure usando o Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). 

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Criar um novo projeto ASP.NET no Visual Studio

1. No computador executando o Visual Studio, escolha **arquivo > Novo projeto**.

1. Em **Visual C#** ou **Visual Basic**, escolha **Web**e, em seguida, no painel central, escolha um **o aplicativo Web do ASP.NET (.NET Framework)** ou (c# somente) **aplicativo Web do ASP.NET Core**e, em seguida, clique em **Okey**.

    Se você não vir os modelos de projeto especificado, clique no **abrir instalador do Visual Studio** link no painel esquerdo do **novo projeto** caixa de diálogo. O Instalador do Visual Studio é iniciado. Consulte os pré-requisitos deste artigo para identificar as cargas de trabalho de Visual Studio necessárias, que deve ser instalado.

1. Escolha **MVC** (.NET Framework) ou **aplicativo Web (Model-View-Controller)** (para .NET Core) e certifique-se de que **sem autenticação** está selecionado e, em seguida, clique em **Okey**.

1. Digite um nome como **MyWebApp** e clique em **Okey**.

    O Visual Studio cria o projeto.

1. Escolha **Construir > Compilar solução** para compilar o projeto.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Criar o arquivo de configurações de publicação no serviço de aplicativo do Azure

1. No portal do Azure, abra o serviço de aplicativo do Azure.

1. Clique em **obter perfil de publicação** e salve o perfil localmente.

    ![Obter o perfil de publicação](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Um arquivo com um *. publishsettings* extensão de arquivo foi gerada no local onde você salvou. O código a seguir mostra um exemplo parcial do arquivo (em uma formatação mais legível).

    ```xml
    <publishData>
      <publishProfile
        profileName="DeployASPDotNetCore - Web Deploy"
        publishMethod="MSDeploy"
        publishUrl="deployaspdotnetcore.scm.azurewebsites.net:443"
        msdeploySite="DeployASPDotNetCore"
        userName="$DeployASPDotNetCore"
        userPWD="abcdefghijklmnopqrstuzwxyz"
        destinationAppUrl="http://deployaspdotnetcore20180508031824.azurewebsites.net"
        SQLServerDBConnectionString=""
        mySQLDBConnectionString=""
        hostingProviderForumLink=""
        controlPanelLink="http://windows.azure.com"
        webSystem="WebSites">
        <databases />
      </publishProfile>
    </publishData>
    ```
    Normalmente, o arquivo publishsettings anterior contém dois perfis de publicação que você pode usar no Visual Studio, um para a implantação usando a implantação da Web e um implantar usando o FTP. O código anterior mostra o perfil de implantação da Web. Ambos os perfis serão importados mais tarde ao importar o perfil.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar as configurações de publicação no Visual Studio e implantar

1. No computador em que o projeto ASP.NET aberto no Visual Studio, clique com botão direito no projeto no Gerenciador de soluções e escolha **publicar**.

1. Se você tiver configurado anteriormente quaisquer perfis de publicação, o **publicar** painel é exibido. Clique em **criar novo perfil**.

1. No **escolher um destino de publicação** caixa de diálogo, clique em **importar perfil**.

    ![Escolher publicar](../deployment/media/tutorial-publish-tool-import-profile.png)

1. Navegue até o local do arquivo de configurações de publicação que você criou na seção anterior.

1. No **importar o arquivo de configurações de publicação** caixa de diálogo, selecione o perfil que você criou na seção anterior e clique em **abrir**.

1. Selecione um dos dois perfis importados e, em seguida, clique em **publicar**.

    O Visual Studio inicia o processo de implantação e a janela de saída mostra o progresso e os resultados.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você criou um arquivo de configurações de publicação, importá-la para o Visual Studio e implantado um aplicativo ASP.NET para o serviço de aplicativo do Azure.

> [!div class="nextstepaction"]
> [Introdução à implantação](../deployment/deploying-applications-services-and-components.md)
