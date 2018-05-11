---
title: Publicar em um site da Web - Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/22/2017
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6fa914b1b6b353d4e15bd8293f1fc141dd0ae371
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/10/2018
---
# <a name="publish-a-web-app-or-a-net-core-app-to-a-web-site-using-the-visual-studio-publish-tool"></a>Publicar um aplicativo web ou um aplicativo .NET Core em um site usando a ferramenta de publicação do Visual Studio

Você pode usar o **publicar** ferramenta para publicar aplicativos ASP.NET em um site.

Essas etapas se aplicam ao ASP.NET, ASP.NET Core, .NET Core e aplicativos de Python no Visual Studio. Para Node. js, as etapas são suportadas, mas a interface do usuário é diferente.

## <a name="prerequisites"></a>Pré-requisitos

* Você deve ter o Visual Studio de 2017 instalado e o **ASP.NET** e **do .NET Framework** cargas de trabalho de desenvolvimento. Para um aplicativo .NET Core, você também precisa de **.NET Core** carga de trabalho.

    Se você ainda não instalou o Visual Studio, clique [aqui](http://www.visualstudio.com) para instalá-lo gratuitamente.

## <a name="create-a-new-project"></a>Criar um novo projeto 

1. No Visual Studio, escolha **Arquivo > Novo Projeto**.

1. Em **Visual C#** ou **Visual Basic**, escolha **Web**e, em seguida, no painel central, escolha um **o aplicativo Web do ASP.NET (.NET Framework)** ou (c# somente) **aplicativo Web do ASP.NET Core**e, em seguida, clique em **Okey**.

1. Escolha **MVC** (ou escolha **aplicativo Web (Model-View-Controller)** para .NET Core), certifique-se de que **sem autenticação** está selecionado e, em seguida, clique em **Okey** .

1. Digite um nome como **MyWebApp** e clique em **Okey**.

    O Visual Studio cria o projeto.

1. Escolha **Construir > Compilar solução** para compilar o projeto.

## <a name="publish-to-a-web-site"></a>Publicar em um site da web

1. No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **Publicar**.

    ![Escolher publicar](../deployment/media/quickstart-publish-aspnet.png "escolher publicar")

1. Se você tiver configurado anteriormente quaisquer perfis de publicação, o **publicar** painel é exibido. Clique em **criar novo perfil**.

1. No **escolher um destino de publicação** caixa de diálogo caixa, escolha **IIS, FTP, etc**.

    ![Escolha o IIS, FTP, etc.](../deployment/media/quickstart-publish-iis-ftp.png "escolha IIS, FTP, etc.")

1. Clique em **Publicar**.

    Abre a caixa de diálogo de configurações de publicação do perfil.

    ![Escolha a pasta](../deployment/media/quickstart-publish-settings-web.png "Escolher pasta")

1. No **publicar método** campo, escolha um método como **implantação da Web** ou **FTP**.

    As configurações que você vê próxima correspondem ao seu método de publicação. A implantação da Web simplifica a implantação de aplicativos Web e sites para servidores IIS e deve ser instalada como um aplicativo no servidor. Use o [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx) para instalá-lo.

1. Configurar as configurações necessárias para o método de publicação e clique em **Conexão validar**.

    Se o servidor ou o destino estiver disponível e as configurações estão corretas, você verá uma mensagem que indica a conexão for validada, e você está pronto para publicar.

    ![Validar sua conexão](../deployment/media/quickstart-publish-web-deploy.png "validar sua conexão")

1. Se você quiser definir outras configurações de implantação, clique em **configurações**.

    Você pode configurar opções de como implantar uma configuração de Debug ou Release e, em seguida, clique em **salvar**. Se você estiver depurando remotamente, uma configuração de depuração é necessária.

1. Para publicar, clique em **publicar**.

    A janela de saída mostra os resultados e o progresso da implantação.

## <a name="next-steps"></a>Próximas etapas

Este guia de início rápido, você aprendeu a usar o Visual Studio para criar um perfil de publicação. Você também pode configurar a publicação de uma perfil com a importação de configurações de publicação.

> [!div class="nextstepaction"]
> [Importar configurações de publicação e implantar em IIS](tutorial-import-publish-settings-iis.md)
