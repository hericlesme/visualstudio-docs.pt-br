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
ms.openlocfilehash: e6df935578955d3c72b6f4fa61efdf614229bca0
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808459"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Publicar um aplicativo no IIS, importando as configurações de publicação no Visual Studio

Você pode usar o **publicar** ferramenta para importar configurações de publicação e, em seguida, implante seu aplicativo. Neste artigo, podemos usar configurações de publicação para IIS, mas você pode usar etapas semelhantes para importar configurações de publicação para [serviço de aplicativo do Azure](../deployment/tutorial-import-publish-settings-azure.md). Em alguns cenários, use um perfil de configurações pode ser mais rápido do que configurar manualmente a implantação do IIS para cada instalação do Visual Studio de Publish.

Essas etapas se aplicam a aplicativos ASP.NET, ASP.NET Core e .NET Core no Visual Studio. As etapas correspondem ao Visual Studio 2017 versão 15.6.

Neste tutorial, você irá:

> [!div class="checklist"]
> * Configurar o IIS para que você possa gerar um arquivo de configurações de publicação
> * Criar um arquivo de configurações de publicação
> * Importar o arquivo de configurações de publicação no Visual Studio
> * Implantar o aplicativo no IIS

Um arquivo de configurações de publicação (*\*publishsettings*) é diferente de um perfil de publicação (*\*. pubxml*) criados no Visual Studio. Um arquivo de configurações de publicação é criado pelo IIS ou serviço de aplicativo do Azure, ou podem ser criado manualmente e, em seguida, ele pode ser importado para o Visual Studio.

> [!NOTE]
> Se você precisar apenas copiar um perfil de publicação do Visual Studio (\*arquivo. pubxml) de uma instalação do Visual Studio para outro, você pode encontrar o perfil de publicação  *\<profilename\>. pubxml*, no  *\\< projectname\>\Properties\PublishProfiles* pasta para os tipos de projeto gerenciado. Para sites, procure o *\App_Data* pasta. Os perfis de publicação são arquivos XML do MSBuild.

## <a name="prerequisites"></a>Pré-requisitos

* Você deve ter o Visual Studio 2017 instalado e o **ASP.NET** e **.NET Framework** carga de trabalho de desenvolvimento. Para um aplicativo .NET Core, você também precisa de **.NET Core** carga de trabalho.

    Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalá-lo gratuitamente.

* Para gerar o arquivo de configurações de publicação do IIS, você deve ter um computador que executa o Windows Server 2012 ou Windows Server 2016, e você deve ter a função de servidor Web do IIS configurada corretamente. ASP.NET 4.5 ou ASP.NET Core também deve ser instalado. Para o ASP.NET Core, consulte [publicar no IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). Para o ASP.NET 4.5, consulte [IIS 8.0 usando ASP.NET 3.5 e ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Criar um novo projeto ASP.NET no Visual Studio

1. No computador executando o Visual Studio, escolha **arquivo** > **novo projeto**.

1. Sob **Visual c#** ou **Visual Basic**, escolha **Web**e, em seguida, no painel central, escolha o **aplicativo Web ASP.NET (.NET Framework)** ou (somente c#) **aplicativo Web ASP.NET Core**e, em seguida, clique em **Okey**.

    Clique se você não vir os modelos de projeto especificado, o **abrir instalador do Visual Studio** link no painel esquerdo do **novo projeto** caixa de diálogo. O Instalador do Visual Studio é iniciado. Consulte os pré-requisitos deste artigo para identificar as cargas de trabalho de Visual Studio necessárias, que deve ser instalado.

1. Escolha **MVC** (.NET Framework) ou **aplicativo Web (Model-View-Controller)** (para .NET Core) e certifique-se de que **sem autenticação** está selecionado e, em seguida, clique em **Okey**.

1. Digite um nome como **MyWebApp** e clique em **Okey**.

    O Visual Studio cria o projeto.

1. Escolher **construir** > **compilar solução** para compilar o projeto.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Instalar e configurar a implantação da Web no Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Criar o arquivo de configurações de publicação no IIS no Windows Server

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar as configurações de publicação no Visual Studio e implantar

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Depois que o aplicativo é implantado com êxito, ele deve ser iniciado automaticamente. Se ele não for iniciado do Visual Studio, inicie o aplicativo no IIS. Para o ASP.NET Core, você precisará certificar-se de que o pool de aplicativos de campo para o **DefaultAppPool** é definido como **sem código gerenciado**.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você criou um arquivo de configurações de publicação, importou para o Visual Studio e implantado um aplicativo ASP.NET no IIS. Talvez você queira uma visão geral das outras opções de publicação no Visual Studio.

> [!div class="nextstepaction"]
> [Introdução à implantação](../deployment/deploying-applications-services-and-components.md)
