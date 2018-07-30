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
ms.openlocfilehash: aa4afce6ef50284f1f966054e805b55c86f4daaf
ms.sourcegitcommit: 4f82c178b1ac585dcf13b515cc2a9cb547d5f949
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2018
ms.locfileid: "39341742"
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

## <a name="clean-up-resources"></a>Limpar recursos

Nas etapas anteriores, você criou os recursos do Azure em um grupo de recursos. Se você não espera precisar desses recursos no futuro, você pode excluí-los ao excluir o grupo de recursos.
No menu à esquerda no portal do Azure, selecione **grupos de recursos** e, em seguida, selecione **myResourceGroup**.
Na página do grupo de recursos, certifique-se de que os recursos listados são aqueles que deseja excluir.
Selecione **exclua**, digite **myResourceGroup** na caixa de texto e, em seguida, selecione **excluir**.

## <a name="next-steps"></a>Próximas etapas

Neste início rápido, você aprendeu a usar o Visual Studio para criar um perfil de publicação para implantação no serviço de aplicativo no Linux. Você poderá obter mais informações sobre a publicação para Linux usando o Azure.

> [!div class="nextstepaction"]
> [Serviço de Aplicativo do Linux](/azure/app-service/containers/app-service-linux-intro)
