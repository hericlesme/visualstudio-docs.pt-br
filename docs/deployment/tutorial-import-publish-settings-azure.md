---
title: Publicar no Azure com a importação de configurações de publicação
ms.description: Create and import a publishing profile to deploy an application from Visual Studio to Azure App Service
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
ms.openlocfilehash: 2b4b0e4ea963f20199267f32a8c87440c8cc350b
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808315"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Publicar um aplicativo no serviço de aplicativo do Azure importando as configurações de publicação no Visual Studio

Você pode usar o **publicar** ferramenta para importar configurações de publicação e, em seguida, implante seu aplicativo. Neste artigo, podemos usar configurações de publicação para o serviço de aplicativo do Azure, mas você pode usar etapas semelhantes para importar configurações de publicação [IIS](../deployment/tutorial-import-publish-settings-iis.md). Em alguns cenários, use um perfil de configurações pode ser mais rápido do que a configuração manual de implantação para o serviço para cada instalação do Visual Studio de Publish.

Essas etapas se aplicam a aplicativos ASP.NET, ASP.NET Core e .NET Core no Visual Studio. Você também pode importar as configurações de publicação [Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md) aplicativos. As etapas correspondem ao Visual Studio 2017 versão 15.6.

Neste tutorial, você irá:

> [!div class="checklist"]
> * Gerar um arquivo de configurações de publicação do serviço de aplicativo do Azure
> * Importar o arquivo de configurações de publicação no Visual Studio
> * Implantar o aplicativo no serviço de aplicativo do Azure

Um arquivo de configurações de publicação (*\*publishsettings*) é diferente de um perfil de publicação (*\*. pubxml*) criados no Visual Studio. Um arquivo de configurações de publicação é criado pelo serviço de aplicativo do Azure e, em seguida, ele pode ser importado para o Visual Studio.

> [!NOTE]
> Se você precisar apenas copiar um perfil de publicação do Visual Studio (*\*. pubxml* arquivo) de uma instalação do Visual Studio para outro, você pode encontrar o perfil de publicação  *\<profilename\>. pubxml*, no  *\\< projectname\>\Properties\PublishProfiles* pasta para os tipos de projeto gerenciado. Para sites, procure o *\App_Data* pasta. Os perfis de publicação são arquivos XML do MSBuild.

## <a name="prerequisites"></a>Pré-requisitos

* Você deve ter o Visual Studio 2017 instalado e o **ASP.NET** e. **NET Framework** carga de trabalho de desenvolvimento. Para um aplicativo .NET Core, você também precisa de. **NET Core** carga de trabalho.

    Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalá-lo gratuitamente.

* Crie um serviço de aplicativo do Azure. Para obter instruções detalhadas, consulte [implantar um aplicativo web ASP.NET Core no Azure usando o Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Criar um novo projeto ASP.NET no Visual Studio

1. No computador executando o Visual Studio, escolha **arquivo** > **novo projeto**.

1. Sob **Visual c#** ou **Visual Basic**, escolha **Web**e, em seguida, no painel central, escolha o **aplicativo Web ASP.NET (.NET Framework)** ou (somente c#) **aplicativo Web ASP.NET Core**e, em seguida, clique em **Okey**.

    Clique se você não vir os modelos de projeto especificado, o **abrir instalador do Visual Studio** link no painel esquerdo do **novo projeto** caixa de diálogo. O Instalador do Visual Studio é iniciado. Consulte os pré-requisitos deste artigo para identificar as cargas de trabalho de Visual Studio necessárias, que deve ser instalado.

1. Escolha **MVC** (.NET Framework) ou **aplicativo Web (Model-View-Controller)** (para .NET Core) e certifique-se de que **sem autenticação** está selecionado e, em seguida, clique em **Okey**.

1. Digite um nome como **MyWebApp** e clique em **Okey**.

    O Visual Studio cria o projeto.

1. Escolher **construir** > **compilar solução** para compilar o projeto.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Criar o arquivo de configurações de publicação no serviço de aplicativo do Azure

1. No portal do Azure, abra o serviço de aplicativo do Azure.

1. Clique em **obter perfil de publicação** e salve o perfil localmente.

    ![Obter o perfil de publicação](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Um arquivo com um *. publishsettings* extensão de arquivo foi gerada no local onde ele foi salvo. O código a seguir mostra um exemplo parcial do arquivo (em uma formatação mais legível).

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
    Normalmente, o arquivo publishsettings anterior contém dois perfis de publicação que você pode usar no Visual Studio, uma para implantar usando a implantação da Web e outro para implantar usando o FTP. O código anterior mostra o perfil de implantação da Web. Os dois perfis serão importados mais tarde ao importar o perfil.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar as configurações de publicação no Visual Studio e implantar

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você criou um arquivo de configurações de publicação, importou para o Visual Studio e implantado um aplicativo ASP.NET no serviço de aplicativo do Azure. Talvez você queira uma visão geral das opções de publicação no Visual Studio.

> [!div class="nextstepaction"]
> [Introdução à implantação](../deployment/deploying-applications-services-and-components.md)
