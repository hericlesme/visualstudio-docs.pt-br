---
title: Implantar usando a implantação da Web
description: Implantar um aplicativo usando a implantação da Web no Visual Studio
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 8c843ffa6abcb7517ebfe7cdfb0e742a5f244e07
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2018
ms.locfileid: "34478308"
---
Se você instalou a implantação da Web usando o Web Platform Installer, você pode implantar o aplicativo diretamente do Visual Studio.

1. Inicie o Visual Studio com privilégios de administrador e, em seguida, reabra o projeto.

    São necessários privilégios de administrador para implantar seu aplicativo usando a implantação da Web.

1. No **Solution Explorer**, com o botão direito no nó do projeto e selecione **publicar**.

    Se você tiver configurado anteriormente quaisquer perfis de publicação, o **publicar** painel é exibido. Clique em **novo perfil**.

1. Para **selecionar um destino de publicação**, selecione **IIS, FTP, etc.** e clique em **publicar**.

    ![RemoteDBG_Publish_IISl](../media/remotedbg_iis_profile.png "RemoteDBG_Publish_IIS")

1. Insira os parâmetros de configuração de correção para a instalação do IIS.

    ![RemoteDBG_Publish_WebDeployl](../media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Se um nome de host não resolver ao tentar validar na próxima etapas no **Server** texto caixa, tente o endereço IP. Incluir `http://` como um prefixo de **Server** campo.  Verifique se você usa a porta 80 no **Server** texto caixa e certifique-se de que a porta 80 está aberta no firewall.

1. Clique em **próximo**, escolha um **depurar** configuração e escolha **remover arquivos adicionais no destino** sob o **Publicar arquivo** Opções.

    > [!NOTE]
    > Se você escolher uma configuração de versão, você desabilitar depuração no arquivo Web. config quando você publicar.

1. Clique em **Prev**e, em seguida, escolha **validar**. Se a configuração de conexão for validado, você pode tentar publicar.

1. Clique em **publicar** para publicar o aplicativo.

    A guia saída mostra se a publicação foi bem-sucedida e o navegador abre o aplicativo.

    Se você receber um erro mencionar a implantação da Web, verifique novamente as etapas de instalação de implantação da Web e verifique se as portas corretas estão abertas (também implantação da Web requer a porta 8172 sejam abertos no servidor).

    Se o aplicativo implanta com êxito, mas não funcionar corretamente, pode haver um problema com a configuração do IIS, a instalação do ASP.NET ou sua configuração de site da Web. No Windows Server, abra o site da Web do IIS para mensagens de erro mais específicas e, em seguida, verifique novamente as etapas anteriores.
