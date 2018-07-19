---
title: Tour pelos recursos de implantação
description: Saiba mais sobre as opções de implantação de aplicativos do Visual Studio.
ms.custom: mvc
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET applications, deploying
- components [Visual Studio], deploying
- installers
- publishing
- deploying applications [Visual Studio]
- deploying applications [Visual Studio], about deploying applications
- components [.NET Framework], deploying
ms.assetid: 63fcdd5b-2e54-4210-9038-65bc23167725
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9198e39be5149440b09ebab5115e803d60716423
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080257"
---
# <a name="quickstart-first-look-at-deployment-in-visual-studio"></a>Guia de início rápido: Introdução à implantação no Visual Studio

Ao implantar um aplicativo, serviço ou componente, distribuí-lo para instalação em outros computadores, dispositivos ou servidores ou na nuvem. Você escolhe o método apropriado no Visual Studio para o tipo de implantação que deseja. (Muitos tipos de aplicativo dar suporte a outras ferramentas de implantação como implantação de linha de comando ou o NuGet não são descritas aqui.)

Consulte os guias de início rápido e tutoriais para obter instruções passo a passo de implantação. Para obter uma visão geral das opções de implantação, consulte [quais opções de publicação são adequadas para mim?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me).

## <a name="deploy-to-local-folder"></a>Implantar em pasta local

Implantação em uma pasta local é normalmente usada para teste ou para iniciar uma implantação de preparo em que outra ferramenta é usada para a implantação final.

- **ASP.NET**, **Core ASP.NET**, **Node. js**, **Python**, e. **NET Core**: usar a ferramenta de publicação para implantar em uma pasta local. As opções exatas disponíveis dependem de seu tipo de aplicativo. No Gerenciador de soluções, clique em seu projeto e escolha **publicar**. (Se você já tiver configurado qualquer perfil de publicação, você deve clicar em **criar novo perfil**.) Em seguida, escolha **pasta**. Para obter mais informações, consulte [implantar em uma pasta local](quickstart-deploy-to-local-folder.md).

    ![Escolha publicar](../deployment/media/quickstart-publish.png)

- **Tempo de execução do Visual C++**: você pode implantar o tempo de execução do Visual C++ usando a implantação local ou vinculação estática. Para obter mais informações, consulte [implantação de área de trabalho aplicativos nativos (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp). 

## <a name="publish-to-azure"></a>Publicar no Azure

- **ASP.NET**, **Core ASP.NET**, **Python**, e **Node. js**: você pode usar a ferramenta de publicação para implantar rapidamente aplicativos para o serviço de aplicativo do Azure ou para uma Virtual do Azure Máquina. No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **Publicar**. (Se você já tiver configurado qualquer perfil de publicação, você deve clicar em **criar novo perfil**.) Na caixa de diálogo Publicar, escolha **serviço de aplicativo** ou **máquinas virtuais do Azure**e, em seguida, siga as etapas de configuração.

    ![Escolha o serviço de aplicativo do Azure](../deployment/media/quickstart-publish-azure.png "escolher serviço de aplicativo do Azure")

    No Visual Studio 2017 versão 15.7 e posteriores, você poderá implantar aplicativos ASP.NET Core **serviço de aplicativo para Linux**.

    Para aplicativos de Python, consulte também [Python – publicar no serviço de aplicativo do Azure](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json).

    Para obter informações sobre como importar um perfil de publicação do serviço de aplicativo do Azure para o Visual Studio, consulte [importar configurações de publicação e implantar no Azure](../deployment/tutorial-import-publish-settings-azure.md).

    Para obter uma introdução rápida, consulte [publicar no Azure](quickstart-deploy-to-azure.md). Consulte também [publicar um aplicativo ASP.NET Core no Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Para implantação usando o Git, consulte [implantação contínua do ASP.NET Core no Azure com o Git](/aspnet/core/publishing/azure-continuous-deployment).

    > [!NOTE]
    > Se você ainda não tiver uma conta do Azure, você poderá [Inscreva-se aqui](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

## <a name="publish-to-web-or-deploy-to-network-share"></a>Publicar na Web ou implantar para compartilhamento de rede

- **ASP.NET**, **Core ASP.NET**, **Node. js**, e **Python**: você pode usar a ferramenta de publicação para implantar um site usando FTP ou implantação da Web. Para obter mais informações, consulte [implantar um site da web](quickstart-deploy-to-a-web-site.md).

    No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **Publicar**. (Se você já tiver configurado qualquer perfil de publicação, você deve clicar em **criar novo perfil**.) Na ferramenta de publicação, escolha a opção desejada e siga as etapas de configuração.

    ![Escolha o IIS, FTP, etc.](../deployment/media/quickstart-publish-iis-ftp.png)

    Para obter informações sobre como importar um perfil de publicação no Visual Studio, consulte [importar configurações de publicação e implantar no IIS](../deployment/tutorial-import-publish-settings-iis.md).

    Você também pode implantar aplicativos ASP.NET e serviços em um número de outras maneiras. Para obter mais informações, consulte [ASP.NET Implantando aplicativos e serviços web](http://www.asp.net/aspnet/overview/deployment).

- **Tempo de execução do Visual C++**: você pode implantar o tempo de execução do Visual C++ usando implantação central. Para obter mais informações, consulte [implantação de área de trabalho aplicativos nativos (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp). 

- **Área de trabalho do Windows** você pode publicar um aplicativo de desktop do Windows para um servidor web ou um compartilhamento de arquivos de rede usando o ClickOnce. Os usuários podem, então, instalar o aplicativo com um único clique. Para obter mais informações, consulte [implantar um aplicativo da área de trabalho usando o ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) e [implantar um aplicativo nativo usando o ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).

## <a name="publish-to-microsoft-store"></a>Publicar no Microsoft Store

No Visual Studio, você pode criar pacotes de aplicativos para implantação no Microsoft Store.

- **UWP**: você pode empacotar seu aplicativo e implantá-lo usando os itens de menu. Para obter mais informações, consulte [empacotar um aplicativo UWP usando o Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Criar um pacote de aplicativos](../deployment/media/feature-tour-create-app-package.jpg)

- **Área de trabalho do Windows**: você pode implantar para a Microsoft Store usando a ponte da área de trabalho a partir do Visual Studio 2017 versão 15.4. Para fazer isso, comece criando um projeto de empacotamento de aplicativo do Windows. Para obter mais informações, consulte [empacotar um aplicativo da área de trabalho para o Microsoft Store (ponte de Desktop)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Ponte da área de trabalho](../deployment/media/feature-tour-desktop-bridge.png)

## <a name="deploy-to-a-device-uwp"></a>Implantar em um dispositivo (UWP)

Se você estiver implantando um aplicativo UWP para teste em um dispositivo, consulte [executar aplicativos UWP em um computador remoto no Visual Studio](../debugger/run-windows-store-apps-on-a-remote-machine.md).

## <a name="create-an-installer-package-windows-client"></a>Criar um pacote do instalador (cliente do Windows)

Se precisar de mais uma instalação complexa de um aplicativo da área de trabalho que [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) pode fornecer, você pode criar um pacote do instalador, um projeto de instalação ou um bootstrapper personalizado.

- Um instalador baseado em MSI WiX pode ser criado usando o [WiX Toolset Visual Studio 2017 Extension](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

- [InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) de Flexera Software pode ser usado com o Visual Studio 2017 (Community Edition não tem suporte). Observe que o InstallShield Limited Edition não está mais incluída com o Visual Studio e não há suporte para o Visual Studio 2017: entre em contato com [Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) sobre a disponibilidade futura.

- Se você quiser criar um projeto de instalação (vdproj), instale o [extensão de projetos de instalador do Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- Você pode instalar os componentes de pré-requisitos para aplicativos da área de trabalho por meio da configuração de um instalador genérico, que é conhecido como bootstrapper. Para obter mais informações, consulte [pré-requisitos de implantação do aplicativo](../deployment/application-deployment-prerequisites.md).

## <a name="deploy-to-test-lab"></a>Implantar para o laboratório de teste

Você pode habilitar o desenvolvimento e testes Implantando seus aplicativos em ambientes virtuais mais sofisticados. Para obter mais informações, consulte [teste em um ambiente de laboratório](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

## <a name="devops-deployment"></a>Implantação de DevOps

Em um ambiente de equipe, você pode usar o Visual Studio Team Services (VSTS) para habilitar a implantação contínua do seu aplicativo. Para obter mais informações, consulte [Build e versão](/vsts/build-release/index) e [implantar no Azure](/vsts/deploy-azure/index).

## <a name="deployment-for-other-app-types"></a>Implantação para outros tipos de aplicativos

| Tipo de aplicativo | Cenário de implantação | Link |
| --- | --- | --- |
| **Aplicativo do Office** | Você pode publicar um suplemento do Office no Visual Studio. | [Implantar e publicar seu suplemento do Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Serviço WCF ou OData**  | Outros aplicativos podem usar os serviços RIA WCF que você implanta em um servidor web. | [Desenvolvendo e implantando WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | O LightSwitch não é mais suportado no Visual Studio 2017, mas ainda pode ser implantado do Visual Studio 2015 e anteriores. | [Implantando aplicativos do LightSwitch](http://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) | 

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você executou uma rápida olhada opções de implantação para diferentes aplicativos.

> [!div class="nextstepaction"]
> [Quais opções de publicação são adequadas para mim?](deploying-applications-services-and-components-resources.md#what-publishing-options-are-right-for-me)
