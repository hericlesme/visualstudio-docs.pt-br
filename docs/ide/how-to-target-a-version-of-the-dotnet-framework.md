---
title: "Como definir uma versão do .NET Framework como destino | Microsoft Docs"
ms.custom: 
ms.date: 12/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: f648f07923117b89278ba0e5f44e351b923f7c26
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Como destinar uma versão do .NET Framework

Este documento descreve como destinar a uma versão do .NET Framework quando você cria um projeto e como alterar a versão de destino em um projeto existente do Visual Basic, Visual C# ou Visual F#.

> [!IMPORTANT]
> Para obter informações sobre como alterar a versão de destino de projetos do C++, consulte [Como modificar a estrutura de destino e o conjunto de ferramentas da plataforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

## <a name="targeting-a-version-when-you-create-a-project"></a>Destinando uma versão quando você cria um projeto

Ao criar um projeto, a versão do .NET Framework à qual você o destina determina quais modelos é possível usar.

### <a name="to-target-a-version-when-you-create-a-project"></a>Para destinar uma versão ao criar um projeto

1.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.

2.  Na lista da parte superior da caixa de diálogo **Novo Projeto**, escolha a versão do .NET Framework que você deseja que o projeto tenha como destino.

3.  Na lista de modelos instalados, escolha o tipo de projeto que você deseja criar, nomeie o projeto e escolha o botão **OK**.

    A lista de modelos mostra somente os projetos que são aceitos pela versão do .NET Framework que você escolheu.

## <a name="changing-the-target-version"></a>Alterando a versão de destino

É possível alterar a versão de destino do .NET Framework em um projeto do Visual Basic, Visual C# ou Visual F# seguindo este procedimento.

Para obter informações sobre como alterar a versão de destino de projetos do C++, consulte [Como modificar a estrutura de destino e o conjunto de ferramentas da plataforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset).

### <a name="to-change-the-targeted-version"></a>Para alterar a versão de destino

1.  No **Gerenciador de Soluções**, abra o menu de atalho do projeto que você deseja alterar e, em seguida, escolha **Propriedades**.

    ![Propriedades do Gerenciador de Soluções do Visual Studio](../ide/media/vs_slnexplorer_properties.png "vs_slnExplorer_Properties")

2. Na coluna esquerda da janela Propriedades, escolha a guia **Aplicativo**.

    ![Guia Aplicativo de Propriedades do Aplicativo do Visual Studio](../ide/media/vs_slnexplorer_properties_applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")

    > [!NOTE]
    > Depois de criar um aplicativo UWP, não é possível alterar a versão de destino do Windows ou do .NET Framework.

3.  Na lista **Estrutura de Destino**, escolha a versão desejada.

4.  Na caixa de diálogo de verificação exibida, escolha o botão **Sim**.

    O projeto é descarregado. Quando é recarregado, ele se destina à versão do .NET Framework que você acabou de escolher.

    > [!NOTE]
    > Se seu código contiver referências a outra versão do .NET Framework que não seja a que você o destinou, mensagens de erro poderão aparecer quando você compilar ou executar o código. Para resolver esses erros, você deverá modificar as referências. Consulte [Solução de problemas de erros de definição de destino do .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>Consulte também

[Visão Geral do Visual Studio Multiplataforma](../ide/visual-studio-multi-targeting-overview.md)  
[Solução de problemas com erros de direcionamento do .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)  
[Página Aplicativo, Designer de Projeto (C#)](../ide/reference/application-page-project-designer-csharp.md)  
[Página de Aplicativo, Designer de Projeto (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)  
[Como modificar a estrutura de destino e o conjunto de ferramentas da plataforma (C++)](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset)