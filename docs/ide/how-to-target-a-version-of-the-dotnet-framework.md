---
title: "Definir como destino uma versão do .NET Framework no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 02/06/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework [Visual Studio]
- .NET Framework version [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 03d8b734833fad5a47f0d5517b21a7851d9258a6
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Como definir uma versão do .NET Framework como destino

Este documento descreve como destinar a uma versão do .NET Framework quando você cria um projeto e como alterar a versão de destino em um projeto existente do Visual Basic, C# ou Visual F#.

> [!IMPORTANT]
> Para obter informações sobre como alterar a versão de destino de projetos do C++, consulte [Como modificar a estrutura de destino e o conjunto de ferramentas da plataforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

## <a name="to-target-a-version-when-you-create-a-project"></a>Para destinar uma versão ao criar um projeto

Quando você cria um projeto, as versões do .NET Framework disponíveis dependem de quais versões estão instaladas e o modelo selecionado na caixa de diálogo **Novo Projeto**.

1. Na barra de menus, selecione **Arquivo** > **Novo** > **Projeto...**

1. Na lista de modelos instalados, escolha o tipo de projeto que você deseja criar, e insira um nome para o projeto.

1. Na lista suspensa de **Framework** na parte inferior da caixa de diálogo **Novo Projeto**, escolha a versão do .NET Framework que você deseja que o projeto tenha como destino.

    A lista de estruturas mostra somente as versões que são aplicáveis para o modelo que você escolheu. Alguns tipos de projeto, como .NET Core, não exigem o .NET Framework. Nesses casos, a lista suspensa **Framework** está oculta.

    ![A lista suspensa Estrutura na caixa de diálogo Novo Projeto](media/vside-newproject-framework.png)

1. Escolha o botão **OK**.

## <a name="to-change-the-targeted-version"></a>Para alterar a versão de destino

É possível alterar a versão de destino do .NET Framework em um projeto do Visual Basic, C# ou Visual F# seguindo este procedimento.

Para obter informações sobre como alterar a versão de destino de projetos do C++, consulte [Como modificar a estrutura de destino e o conjunto de ferramentas da plataforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

1. No **Gerenciador de Soluções**, abra o menu de atalho do projeto que você deseja alterar e, em seguida, escolha **Propriedades**.

    ![Propriedades do Gerenciador de Soluções do Visual Studio](../ide/media/vs_slnexplorer_properties.png "vs_slnExplorer_Properties")

1. Na coluna esquerda da janela Propriedades, escolha a guia **Aplicativo**.

    ![Guia Aplicativo de Propriedades do Aplicativo do Visual Studio](../ide/media/vs_slnexplorer_properties_applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")

    > [!NOTE]
    > Depois de criar um aplicativo UWP, não é possível alterar a versão de destino do Windows ou do .NET Framework.

1. Na lista **Estrutura de Destino**, escolha a versão desejada.

1. Na caixa de diálogo de verificação exibida, escolha o botão **Sim**.

    O projeto é descarregado. Quando é recarregado, ele se destina à versão do .NET Framework que você acabou de escolher.

    > [!NOTE]
    > Se seu código contiver referências a outra versão do .NET Framework que não seja a que você o destinou, mensagens de erro poderão aparecer quando você compilar ou executar o código. Para resolver esses erros, você deverá modificar as referências. Consulte [Solução de problemas de erros de definição de destino do .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>Consulte também

[Visão Geral do Visual Studio Multiplataforma](../ide/visual-studio-multi-targeting-overview.md)  
[Solução de problemas com erros de direcionamento do .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)  
[Página Aplicativo, Designer de Projeto (C#)](../ide/reference/application-page-project-designer-csharp.md)  
[Página de Aplicativo, Designer de Projeto (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)  
[Como modificar a estrutura de destino e o conjunto de ferramentas da plataforma (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)