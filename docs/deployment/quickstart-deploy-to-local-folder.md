---
title: Implantar em uma pasta local
ms.custom: ''
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 517698aa2e042d74138579dae3633930b338cd61
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38781907"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>Implantar um aplicativo em uma pasta local usando o Visual Studio

Você pode usar o **publicar** ferramenta para publicar aplicativos ASP.NET, ASP.NET Core, .NET Core e Python em uma pasta local do Visual Studio. Para Node. js, as etapas têm suporte, mas a interface do usuário é diferente.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="deploy-to-a-local-folder"></a>Implantar em uma pasta local

1. No Gerenciador de soluções, clique com botão direito no projeto e escolha **Publish** (ou usar o **compilação** > **publicar** item de menu).

    ![O comando Publicar no menu de contexto do projeto no Gerenciador de soluções](../deployment/media/quickstart-publish.png "escolher publicar")

1. Se você já tiver configurado qualquer perfil de publicação, o **publicar** painel será exibido. Selecione **criar novo perfil**.

1. No **escolher um destino de publicação** diálogo caixa, escolha **pasta**.

    ![Escolha a pasta local como um destino de publicação](../deployment/media/quickstart-publish-folder.png "Escolher pasta")

1. Insira um caminho ou selecione **procurar** para especificar uma pasta local.

1. Selecione **Publicar**. Visual Studio compila o projeto e publica a pasta especificada. As propriedades do projeto **publicar** painel aparece, mostrando um perfil de resumo.

    ![Publicar o painel de propriedade mostrando um perfil de resumo](../deployment/media/quickstart-publish-folder-summary.png)

1. Para configurar as configurações de implantação, selecione **configurar** no perfil de resumo e selecione o **configurações** guia.

    ![Configurações de perfil](../deployment/media/quickstart-profile-settings.png "as configurações de perfil")

1. Configurar opções de como implantar uma configuração de depuração ou lançamento e, em seguida, selecione **salvar**.

1. Para republicar, selecione **publicar**.

Implante os arquivos publicados na maneira que desejar. Por exemplo, você pode empacotá-las em um *. zip* de arquivo, use um comando de cópia simples ou implantá-los com qualquer pacote de instalação de sua escolha.

## <a name="next-steps"></a>Próximas etapas

- [Implantar um aplicativo do .NET Core com a ferramenta Publicar](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Empacotar um aplicativo da área de trabalho para a Microsoft Store (Ponte de Desktop)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET) [Implantar o .NET Framework e aplicativos](/dotnet/framework/deployment/)
