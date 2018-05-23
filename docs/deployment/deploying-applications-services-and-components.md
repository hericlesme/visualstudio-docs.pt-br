---
title: Visão geral da implantação
description: Saiba mais sobre as opções de implantação de aplicativos do Visual Studio.
ms.custom: mvc
ms.date: 11/26/2017
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
ms.openlocfilehash: 0136fb8f7b1075d2eadeaed10ab26026395b9671
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2018
---
# <a name="quickstart-first-look-at-deployment-in-visual-studio"></a>Início rápido: Primeiro examinar a implantação no Visual Studio

Ao implantar um aplicativo, serviço ou componente, você o distribui para instalação em outros computadores, dispositivos, servidores ou na nuvem. Você escolhe o método apropriado no Visual Studio para o tipo de implantação que deseja. (O muitos tipos de aplicativo oferecer suporte a outras ferramentas de implantação, como implantação de linha de comando ou NuGet que não são descritas aqui.)

Consulte os tutoriais para obter instruções passo a passo.

### <a name="deploy-to-local-folder"></a>Implantar na pasta local

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python**, e **.NET Core**: usar a ferramenta de publicação para implantar em uma pasta local. As opções exatas disponíveis dependem de seu tipo de aplicativo. No Gerenciador de soluções, clique com o botão direito e escolha **publicar**. (Se você já tiver configurado qualquer perfil de publicação, você deve clicar em **criar novo perfil**.) Em seguida, escolha **pasta**. Para obter mais informações, consulte [implantar em uma pasta local](quickstart-deploy-to-local-folder.md).

    ![Escolher publicar](../deployment/media/quickstart-publish.png)

- **Tempo de execução do Visual C++**: você pode implantar o tempo de execução do Visual C++ usando a implantação local ou a vinculação estática. Para obter mais informações, consulte [implantação de área de trabalho aplicativos nativos (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp). 

### <a name="publish-to-web-or-deploy-to-network-share"></a>Publicar na Web ou implantar para compartilhamento de rede

- **ASP.NET**, **ASP.NET Core**, **Node.js**, **Python**, e **.NET Core**: você pode usar a ferramenta de publicação para implantar um site da Web usando FTP ou implantação da Web. Para obter mais informações, consulte [implantar um site da web](quickstart-deploy-to-a-web-site.md).

    No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **Publicar**. (Se você já tiver configurado qualquer perfil de publicação, você deve clicar em **criar novo perfil**.) Na ferramenta de publicação, escolha a opção desejada e siga as etapas de configuração.

    ![Escolha o IIS, FTP, etc.](../deployment/media/quickstart-publish-iis-ftp.png)

    Para obter informações sobre como importar um perfil de publicação no Visual Studio, consulte [importar configurações de publicação e implantar para IIS](../deployment/tutorial-import-publish-settings-iis.md).

    Você também pode implantar aplicativos ASP.NET e serviços em um número de outras maneiras. Para obter mais informações, consulte [serviços e aplicativos web ASP.NET implantando](http://www.asp.net/aspnet/overview/deployment).

- **Tempo de execução do Visual C++**: você pode implantar o tempo de execução do Visual C++ usando a implantação central. Para obter mais informações, consulte [implantação de área de trabalho aplicativos nativos (Visual C++)](/cpp/ide/deploying-native-desktop-applications-visual-cpp). 

- **Área de trabalho do Windows** você pode publicar um aplicativo de área de trabalho do Windows para um servidor web ou um compartilhamento de arquivos de rede usando a implantação do ClickOnce. Os usuários podem, então, instalar o aplicativo com um único clique. Para obter mais informações, consulte [implantar um aplicativo de área de trabalho usando o ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) e [implantar um aplicativo nativo usando o ClickOnce](/cpp/ide/clickonce-deployment-for-visual-cpp-applications).

### <a name="publish-to-azure"></a>Publicar no Azure

- **ASP.NET, ASP.NET Core, Python, Node. js e .NET Core** aplicativos da web: você pode usar a ferramenta de publicação para implantar rapidamente aplicativos do serviço de aplicativo do Azure ou para uma máquina Virtual do Azure. No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **Publicar**. (Se você já tiver configurado qualquer perfil de publicação, você deve clicar em **criar novo perfil**.) Na caixa de diálogo Publicar, escolha **serviço de aplicativo do Microsoft Azure** ou **máquinas virtuais do Microsoft Azure**e, em seguida, siga as etapas de configuração.

    ![Escolha o serviço de aplicativo do Azure](../deployment/media/quickstart-publish-azure.png "escolha o serviço de aplicativo do Azure")

    Para obter informações sobre como importar um perfil de publicação do serviço de aplicativo do Azure para o Visual Studio, consulte [importar configurações de publicação e implantar no Azure](../deployment/tutorial-import-publish-settings-azure.md).

    Para obter uma introdução rápida, consulte [publicar no Azure](quickstart-deploy-to-azure.md). Além disso, consulte [publicar um aplicativo do ASP.NET Core para o Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). Para implantação usando o Git, consulte [implantação contínua do ASP.NET Core para o Azure com o Git](/aspnet/core/publishing/azure-continuous-deployment).

    > [!NOTE]
    > Se você não tiver uma conta do Azure, você pode [Inscreva-se aqui](https://azure.microsoft.com/free/?ref=microsoft.com&utm_source=microsoft.com&utm_medium=doc&utm_campaign=visualstudio).

### <a name="publish-to-microsoft-store"></a>Publicar no repositório da Microsoft

No Visual Studio, você pode criar pacotes de aplicativos para implantação no Microsoft Store.

- **UWP**: você pode empacotar seu aplicativo e implantá-lo usando os itens de menu. Para obter mais informações, consulte [empacotar um aplicativo UWP usando o Visual Studio](/windows/uwp/packaging/packaging-uwp-apps).

    ![Criar um pacote de aplicativos](../deployment/media/feature-tour-create-app-package.jpg)

- **Área de trabalho do Windows**: você pode implantar à Microsoft Store usando a ponte de área de trabalho a partir do Visual Studio 2017 versão 15.4. Para fazer isso, comece criando um projeto de empacotamento de aplicativo do Windows. Para obter mais informações, consulte [empacotar um aplicativo de área de trabalho para o Microsoft Store (ponte de área de trabalho)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net).

    ![Ponte de área de trabalho](../deployment/media/feature-tour-desktop-bridge.png)

### <a name="create-an-installer-package-windows-client"></a>Criar um pacote do instalador (cliente do Windows)

Se você exige mais complexas de instalação de um aplicativo de desktop que [ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) pode fornecer, você pode criar um pacote do instalador, um projeto de instalação ou um inicializador personalizado.

- Um instalador baseado em MSI WiX pode ser criado usando o [WiX conjunto de ferramentas do Visual Studio 2017 extensão](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).

- [O InstallShield](https://www.flexerasoftware.com/producer/products/software-installation/installshield-software-installer/tab/requirements) Flexera software podem ser usadas com o Visual Studio 2017 (Community Edition não tem suporte). Observe que o InstallShield Limited Edition não está mais incluída com o Visual Studio e não há suporte para o Visual Studio de 2017; entre em contato com [Flexera Software](http://learn.flexerasoftware.com/content/IS-EVAL-InstallShield-Limited-Edition-Visual-Studio) sobre disponibilidade futura.

- Se você deseja criar um projeto de instalação (vdproj), instale o [extensão de projetos do Visual Studio 2017 instalador](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.MicrosoftVisualStudio2017InstallerProjects#overview).

- Você pode instalar componentes de pré-requisito para aplicativos de desktop por meio da configuração de um instalador genérico, que é conhecido como um bootstrapper. Para obter mais informações, consulte [os pré-requisitos de implantação de aplicativo](../deployment/application-deployment-prerequisites.md).

### <a name="deploy-to-test-lab"></a>Implantar para o laboratório de teste

Você pode habilitar mais sofisticadas de desenvolvimento e teste ao implantar os aplicativos em ambientes virtuais. Para obter mais informações, consulte [teste em um ambiente de laboratório](../test/lab-management/using-a-lab-environment-for-your-application-lifecycle.md).

### <a name="devops-deployment"></a>Implantação de DevOps

Em um ambiente de equipe, você pode usar o Visual Studio Team Services (VSTS) para habilitar a implantação contínua do seu aplicativo. Para obter mais informações, consulte [Build e versão](/vsts/build-release/index) e [implantar no Azure](/vsts/deploy-azure/index).

### <a name="deployment-for-other-app-types"></a>Implantação de outros tipos de aplicativo

| Tipo de aplicativo | Cenário de implantação | Link |
| --- | --- | --- |
| **Aplicativo do Office** | Você pode publicar um suplemento do Office no Visual Studio. | [Implantar e publicar o suplemento do Office](https://dev.office.com/docs/add-ins/publish/publish) |
| **Serviço WCF ou OData**  | Outros aplicativos podem usar os serviços RIA WCF que você implantar em um servidor web. | [Desenvolvendo e implantando WCF Data Services](/dotnet/framework/data/wcf/developing-and-deploying-wcf-data-services) |
| **LightSwitch** | O LightSwitch não tem suporte no Visual Studio de 2017, mas ainda pode ser implantado do Visual Studio 2015 e versões anteriores. | [Implantando aplicativos do LightSwitch](http://msdn.microsoft.com/Library/4818d933-295c-4ecc-9148-7ad9ca28dcdb) | 

