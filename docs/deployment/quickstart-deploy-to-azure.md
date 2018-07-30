---
title: Publicar no Serviço de Aplicativo do Azure
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
- azure
ms.openlocfilehash: a8de7175b33a91c310da4b3d6d9e4c05c40c3522
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341684"
---
# <a name="publish-a-web-app-to-azure-app-service-using-visual-studio"></a>Publicar um aplicativo Web no serviço de aplicativo do Azure usando o Visual Studio

Você pode usar o **publicar** ferramenta para publicar aplicativos ASP.NET, ASP.NET Core, Node. js e .NET Core no serviço de aplicativo do Azure ou serviço de aplicativo do Azure Linux (usando contêineres). Para aplicativos de Python, siga as etapas em [Python – publicar no serviço de aplicativo do Azure](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

[!INCLUDE [quickstart-prereqs-azure](includes/quickstart-prereqs-azure.md)]

## <a name="publish-to-azure-app-service"></a>Publicar no Serviço de Aplicativo do Azure

1. No Gerenciador de soluções, clique com botão direito no projeto e escolha **Publish** (ou usar o **compilação** > **publicar** item de menu).

    ![O comando Publicar no menu de contexto do projeto no Gerenciador de soluções](../deployment/media/quickstart-publish.png "escolher publicar")

1. Se você já tiver configurado qualquer perfil de publicação, o **Publish** painel será exibido, em que select case **criar novo perfil**.

1. No **escolher um destino de publicação** diálogo caixa, escolha **serviço de aplicativo**.

    ![Escolha o serviço de aplicativo do Azure](../deployment/media/quickstart-publish-azure.png "escolher serviço de aplicativo do Azure")

1. Selecione **Publicar**. O **criar serviço de aplicativo** caixa de diálogo é exibida. Entrar com você conta do Azure, se necessário e, em seguida, as configurações de serviço de aplicativo padrão preencher os campos.

    ![Criar serviço de aplicativo](../deployment/media/quickstart-publish-settings-app-service.png "criar serviço de aplicativo do Azure")

1. Selecione **Criar**. Visual Studio implanta o aplicativo em seu serviço de aplicativo do Azure, e o aplicativo web é carregado em seu navegador. As propriedades do projeto **publicar** painel mostra a URL do site e outros detalhes.

    ![Publicar o painel de propriedade mostrando um perfil de resumo](../deployment/media/quickstart-publish-app-service-summary.png)

## <a name="clean-up-resources"></a>Limpar recursos

Nas etapas anteriores, você criou os recursos do Azure em um grupo de recursos. Se você não espera precisar desses recursos no futuro, você pode excluí-los ao excluir o grupo de recursos.
No menu à esquerda no portal do Azure, selecione **grupos de recursos** e, em seguida, selecione **myResourceGroup**.
Na página do grupo de recursos, certifique-se de que os recursos listados são aqueles que deseja excluir.
Selecione **exclua**, digite **myResourceGroup** na caixa de texto e, em seguida, selecione **excluir**.

## <a name="next-steps"></a>Próximas etapas

Neste início rápido, você aprendeu a usar o Visual Studio para criar um perfil de publicação para implantação no Azure. Você também pode configurar a publicação de uma perfil com a importação de configurações de publicação do serviço de aplicativo do Azure.

> [!div class="nextstepaction"]
> [Importar configurações de publicação e implantar no Azure](tutorial-import-publish-settings-azure.md)
