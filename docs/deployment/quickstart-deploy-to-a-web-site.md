---
title: Publicar em um site da Web - Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/22/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e324869eb90cd60cba68d9ed7b2e3fdb1ebb588d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2018
---
# <a name="publish-a-web-app-or-a-net-core-app-to-a-web-site-using-the-visual-studio-publish-tool"></a>Publicar um aplicativo web ou um aplicativo .NET Core em um site usando a ferramenta de publicação do Visual Studio

Você pode usar o **publicar** ferramenta para publicar aplicativos ASP.NET em um site.

Essas etapas se aplicam ao ASP.NET, ASP.NET Core, .NET Core e aplicativos de Python no Visual Studio. Para Node. js, as etapas são suportadas, mas a interface do usuário é diferente.

## <a name="create-a-new-project"></a>Criar um novo projeto 

1. No Visual Studio, escolha **Arquivo > Novo Projeto**.

1. Em **Visual C#** ou **Visual Basic**, escolha **Web**e, em seguida, no painel central, escolha um **o aplicativo Web do ASP.NET (.NET Framework)**ou (c# somente) **aplicativo Web do ASP.NET Core**e, em seguida, clique em **Okey**.

1. Escolha **MVC**, certifique-se de que **sem autenticação** está selecionado e, em seguida, clique em **Okey**.

1. Digite um nome como **MyWebApp** e clique em **Okey**.

    O Visual Studio cria o projeto.

1. Escolha **Construir > Compilar solução** para compilar o projeto.

## <a name="publish-to-a-web-site"></a>Publicar em um site da web

1. No Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **Publicar**.

    ![Escolher publicar](../deployment/media/quickstart-publish-aspnet.png "escolher publicar")

1. No **publicar** painel, escolha **IIS, FTP, etc**.

    ![Escolha o IIS, FTP, etc.](../deployment/media/quickstart-publish-iis-ftp.png "escolha IIS, FTP, etc.")

1. Clique em **Publicar**.

    Abre a caixa de diálogo de configurações de publicação do perfil.

    ![Escolha a pasta](../deployment/media/quickstart-publish-settings-web.png "Escolher pasta")

1. No **publicar método** campo, escolha um método como **implantação da Web** ou **FTP**.

    As configurações que você vê próxima correspondem ao seu método de publicação.

1. Configurar as configurações necessárias para o método de publicação e clique em **Conexão validar**.

    Se o servidor ou o destino estiver disponível e as configurações estão corretas, você verá uma mensagem que indica a conexão for validada, e você está pronto para publicar.

    ![Validar sua conexão](../deployment/media/quickstart-publish-web-deploy.png "validar sua conexão")

1. Se você quiser definir outras configurações de implantação, clique em **configurações**.

    Você pode configurar opções de como implantar uma configuração de Debug ou Release e, em seguida, clique em **salvar**. Se você estiver depurando remotamente, uma configuração de depuração é necessária.

1. Para publicar, clique em **publicar**.

    A janela de saída mostra os resultados e o progresso da implantação.

## <a name="next-steps"></a>Próximas etapas

- [Implantar o ASP.NET no IIS](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)
