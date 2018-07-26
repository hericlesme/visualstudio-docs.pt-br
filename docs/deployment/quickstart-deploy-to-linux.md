---
title: Publicar no serviço de aplicativo no Linux
ms.custom: ''
ms.date: 07/23/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- azure
ms.openlocfilehash: 9f79cef595b3a58426b596fc1019c59b801a02d5
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252356"
---
# <a name="publish-an-aspnet-core-app-to-app-service-on-linux-using-visual-studio"></a>Publicar um aplicativo ASP.NET Core no serviço de aplicativo no Linux usando o Visual Studio

Você pode usar o **publicar** ferramenta para publicar aplicativos ASP.NET Core no serviço de aplicativo do Azure no Linux.

Implantação no serviço de aplicativo no Linux usando o **publicar** ferramenta requer o Visual Studio 2017 versão 15.7.

[!INCLUDE [quickstart-prereqs-azure-linux](includes/quickstart-prereqs-azure-linux.md)]

## <a name="publish-to-app-service-on-linux"></a>Publicar no serviço de aplicativo no Linux

1. No Gerenciador de soluções, clique com botão direito no projeto e escolha **Publish** (ou usar o **compilação** > **publicar** item de menu).

    ![O comando Publicar no menu de contexto do projeto no Gerenciador de soluções](../deployment/media/quickstart-publish.png "escolher publicar")

1. Se você já tiver configurado qualquer perfil de publicação, o **Publish** painel será exibido, em que select case **criar novo perfil**.

1. No **escolher um destino de publicação** diálogo caixa, escolha **serviço de aplicativo Linux**.

    ![Escolha o serviço de aplicativo do Azure](../deployment/media/quickstart-publish-linux.png "escolher serviço de aplicativo do Azure")

1. Selecione **Publicar**. O **criar serviço de aplicativo** caixa de diálogo é exibida. Entrar com você conta do Azure, se necessário e, em seguida, as configurações de serviço de aplicativo padrão preencher os campos.

    ![Criar serviço de aplicativo](../deployment/media/quickstart-publish-settings-app-service-linux.png "criar serviço de aplicativo do Azure")

1. Selecione **Criar**. Visual Studio implanta o aplicativo em seu serviço de aplicativo do Azure, e o aplicativo web é carregado em seu navegador. As propriedades do projeto **publicar** painel mostra a URL do site e outros detalhes.

    ![Publicar o painel de propriedade mostrando um perfil de resumo](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="next-steps"></a>Próximas etapas

Neste início rápido, você aprendeu a usar o Visual Studio para criar um perfil de publicação para implantação no serviço de aplicativo no Linux. Você poderá obter mais informações sobre a publicação para Linux usando o Azure.

> [!div class="nextstepaction"]
> [Serviço de Aplicativo do Linux](/azure/app-service/containers/app-service-linux-intro)
