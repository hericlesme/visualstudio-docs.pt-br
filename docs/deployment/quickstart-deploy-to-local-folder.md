---
title: Implantar em uma pasta local - Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords: deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c8696e7ffb4120bae12538a03b77d62c0d091a7
ms.sourcegitcommit: 64c7682ec3a2cbea684e716803398d4278b591d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/15/2017
---
# <a name="deploy-a-web-app-or-net-core-app-to-a-local-folder-using-the-visual-studio-publish-tool"></a>Implantar um aplicativo web ou aplicativo .NET Core para uma pasta local usando a ferramenta de publicação do Visual Studio

Você pode usar o **publicar** ferramenta para publicar seu aplicativo para uma pasta local. 

Essas etapas se aplicam ao ASP.NET, ASP.NET Core, .NET Core e aplicativos de Python no Visual Studio. Para Node. js, as etapas são suportadas, mas a interface do usuário é diferente.

## <a name="create-a-new-project"></a>Criar um novo projeto 

1. No Visual Studio, escolha **arquivo > Novo projeto**.

1. Em **Visual C#** ou **Visual Basic**, escolha **.NET Core**e, em seguida, no painel central, escolha **aplicativo de Console (.NET Core)**.

1. Digite um nome como **MyLocalApp** e clique em **Okey**.

    O Visual Studio cria o projeto.

## <a name="deploy-to-a-local-folder"></a>Implantar em uma pasta local

1. No Gerenciador de soluções, clique com o botão direito e escolha **publicar**.

    ![Escolher publicar](../deployment/media/quickstart-publish.png "escolher publicar")

1. No **publicar** painel, escolha **pasta**.

    ![Escolha a pasta](../deployment/media/quickstart-publish-folder.png "Escolher pasta")

1. Insira um caminho ou clique em **procurar** para navegar até uma pasta local.

1. Clique em **Publicar**.

    O Visual Studio compila o projeto e publica a pasta especificada.

    O painel de publicação mostra um perfil de resumo.

1. Para definir as configurações de implantação, clique em **configurações** no perfil de resumo.

    ![Configurações de perfil](../deployment/media/quickstart-profile-settings.png "as configurações de perfil") 

1. Configurar opções de como implantar uma configuração de Debug ou Release e, em seguida, clique em **salvar**.

1. Para publicar novamente, clique em **publicar**.

Implante os arquivos publicados na maneira que desejar. Por exemplo, você pode empacotá-las em um arquivo Zip, usar um comando de cópia simples ou implantá-las com qualquer pacote de instalação de sua escolha.

## <a name="next-steps"></a>Próximas etapas

- [Implantar um aplicativo do .NET Core com a ferramenta de publicação](https://docs.microsoft.com/en-us/dotnet/core/deploying/deploy-with-vs)
- [Um aplicativo de área de trabalho do pacote para o Microsoft Store (ponte de área de trabalho)](https://docs.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)
- (.NET) [Implantar o .NET Framework e aplicativos](https://docs.microsoft.com/en-us/dotnet/framework/deployment/)
