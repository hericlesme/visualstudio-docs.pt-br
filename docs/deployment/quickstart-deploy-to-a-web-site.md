---
title: Publicar em um site
ms.custom: ''
ms.date: 06/22/2018
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
ms.openlocfilehash: 036d7549995f79808142c3a0a64e7e5f2075df2c
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077497"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Publicar um aplicativo Web em um site da web usando o Visual Studio

Você pode usar o **publicar** ferramenta para publicar aplicativos ASP.NET, ASP.NET Core, .NET Core e Python em um site do Visual Studio. Para Node. js, as etapas têm suporte, mas a interface do usuário é diferente.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="publish-to-a-web-site"></a>Publicar em um site da Web

1. No Gerenciador de soluções, clique com botão direito no projeto e escolha **Publish** (ou usar o **compilação** > **publicar** item de menu).

    ![O comando Publicar no menu de contexto do projeto no Gerenciador de soluções](../deployment/media/quickstart-publish.png "escolher publicar")

1. Se você já tiver configurado qualquer perfil de publicação, o **publicar** painel será exibido. Selecione **criar novo perfil**.

1. No **escolher um destino de publicação** diálogo caixa, escolha **IIS, FTP, etc**.

    ![Escolha o IIS, FTP, etc.](../deployment/media/quickstart-publish-iis-ftp.png "escolha IIS, FTP, etc.")

1. Selecione **Publicar**. Abre a caixa de diálogo de configurações de publicação do perfil.

    ![Escolher pasta](../deployment/media/quickstart-publish-settings-web.png "Escolher pasta")

1. No **método de publicação** campo, escolha um método, como **implantação da Web** ou **FTP**. Em seguida, as configurações que você vê correspondem a seu método de publicação. A implantação da Web simplifica a implantação de aplicativos Web e sites da Web em servidores IIS e deve ser instalada como um aplicativo no servidor. Use o [instalador de plataforma da Web](https://www.microsoft.com/web/downloads/platform.aspx) para instalá-lo.

1. Defina as configurações necessárias para o método de publicação e selecione **validar Conexão**. Se o servidor ou o destino estiver disponível e as configurações estão corretas, uma mensagem que indica a conexão for validada, e você estiver pronto para publicar.

    ![Validar sua conexão](../deployment/media/quickstart-publish-web-deploy.png "validar sua conexão")

1. Selecione **as configurações** para definir outras configurações de implantação, como se deseja implantar uma configuração de depuração ou versão e, em seguida, selecione **salvar**. Se você estiver depurando remotamente, uma configuração de depuração é necessária.

1. Para publicar, selecione **publicar**. A janela saída mostra os resultados e o progresso da implantação.

## <a name="next-steps"></a>Próximas etapas

Neste início rápido, você aprendeu a usar o Visual Studio para criar um perfil de publicação. Você também pode configurar a publicação de uma perfil com a importação de configurações de publicação.

> [!div class="nextstepaction"]
> [Importar configurações de publicação e implantar no IIS](tutorial-import-publish-settings-iis.md)
