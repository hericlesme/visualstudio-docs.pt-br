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
ms.openlocfilehash: 02e6ae6e06daf43a6aec08097df2b37a21d2aaa3
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766664"
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

Um arquivo de configurações de publicação (*\*. publishsettings*) é diferente de um perfil de publicação (*\*. pubxml*) criado no Visual Studio. Um arquivo de configurações de publicação é criado pelo IIS ou o serviço de aplicativo do Azure, ou pode ser criado manualmente e, em seguida, ele pode ser importado para o Visual Studio.

> [!NOTE]
> Se você só precisa copiar um perfil de publicação do Visual Studio (\*arquivo. pubxml) de uma instalação do Visual Studio para outro, você pode encontrar o perfil de publicação,  *\<profilename\>. pubxml*, no  *\\< projectname\>\Properties\PublishProfiles* pasta para os tipos de projeto gerenciado. Para sites, procure o *\App_Data* pasta. Os perfis de publicação são arquivos XML do MSBuild.

## <a name="prerequisites"></a>Pré-requisitos

* Você deve ter o Visual Studio de 2017 instalado e o **ASP.NET** e **do .NET Framework** cargas de trabalho de desenvolvimento. Para um aplicativo .NET Core, você também precisa de **.NET Core** carga de trabalho.

    Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalá-lo gratuitamente.

* Para gerar o arquivo de configurações de publicação do IIS, você deve ter um computador que executa o Windows Server 2012 ou Windows Server 2016, e você deve ter a função de servidor Web do IIS configurada corretamente. O ASP.NET 4.5 ou o ASP.NET Core também deve ser instalado. Para o ASP.NET Core, consulte [publicar no IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). Para o ASP.NET 4.5, consulte [IIS 8.0 usando ASP.NET 3.5 e o ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

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

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importar as configurações de publicação no Visual Studio e implantar

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Depois que o aplicativo implanta com êxito, ele deve ser iniciado automaticamente. Se ele não for iniciado no Visual Studio, inicie o aplicativo no IIS. Para o ASP.NET Core, você precisa certificar-se de que o pool de aplicativos campo para o **DefaultAppPool** é definido como **sem código gerenciado**.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, criado um arquivo de configurações de publicação, importe-o para o Visual Studio e implantado um aplicativo ASP.NET no IIS. Talvez você queira obter uma visão geral de outras opções de publicação no Visual Studio.

> [!div class="nextstepaction"]
> [Introdução à implantação](../deployment/deploying-applications-services-and-components.md)
