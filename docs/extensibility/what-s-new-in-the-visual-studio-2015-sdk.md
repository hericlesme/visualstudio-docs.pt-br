---
title: O que &#39; s no SDK do Visual Studio 2015 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b8b1fa4647cd5b145d19e2264381b186394be814
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>O que &#39; s no SDK do Visual Studio 2015
O Visual Studio SDK tem os seguintes recursos novos e atualizados para o Visual Studio 2015, Visual Studio 2015 atualizado e 2017 do Visual Studio.  
  
## <a name="vs-2015-sdk-update-1"></a>Atualização do SDK do VS 2015 1  
 Atualização 1 inclui ferramentas para ajudar a sua extensão funcionam bem com temas de cores e o serviço de imagem do Visual Studio.  
  
 Esses tópicos estão sob o [VSSDK utilitários](../extensibility/internals/vssdk-utilities.md) seção:  
  
-   O [ferramentas de temas de cores](../extensibility/internals/color-theming-tools.md) ajudá-lo a criar e editar cores personalizadas para o Visual Studio.  
  
-   O [ferramentas de serviço de imagem](../extensibility/internals/image-service-tools.md) permitem a você trabalhar com arquivos de manifesto de imagem do Visual Studio.  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Nova maneira de adicionar o SDK do Visual Studio para o Visual Studio  
 A partir do Visual Studio 2015, você não precisa fazer o download do SDK do Visual Studio separadamente. Em vez disso, você pode instalá-lo como parte do processo de instalação normal, ou você pode optar por instalá-lo mais tarde. Quando você abre ou cria uma solução VSIX, Visual Studio solicitará que você instale as ferramentas de extensibilidade do Visual Studio. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="new-ways-of-creating-extensions"></a>Novas maneiras de criação de extensões  
 A partir do SDK do Visual Studio 2015, você tem opções diferentes para criar extensões, dependendo da linguagem de programação que você está usando.  
  
### <a name="visual-c-and-visual-basic"></a>Visual C# e Visual Basic  
 Para c# e Visual Basic, há uma ampla gama de modelos de item de projeto que permitem que você crie VSPackages, comandos de menu, janelas de ferramentas, classificadores de editor, editor ornamentos e extensões de margem do editor. Você pode adicionar qualquer ou todos eles para o projeto padrão do VSIX. Para obter mais informações, consulte:  
  
-   [Criar uma extensão com um comando de menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [Criar uma extensão com uma janela de ferramentas](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [Criar uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [Criar uma extensão com um VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     O Assistente de VSPackage não cria mais extensões em c# ou Visual Basic.  
  
### <a name="c"></a>C++  
 Para C++, o Assistente de VSPackage suporte para editores personalizados, janelas de ferramentas e comandos de menu. Procure-na **novo projeto** caixa de diálogo na **Visual C++ / extensibilidade**.  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Assemblies de referência SDK do VS por meio do NuGet  
 Para maior portabilidade e o compartilhamento de projetos de extensibilidade, você pode usar as versões do NuGet dos assemblies de referência do SDK do VS.  Estes estão disponíveis em [nuget.org](http://www.nuget.org) publicado por [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) e podem ser facilmente adicionadas no seu projeto ou solução por meio do Visual Studio **referencia / gerenciar NuGet Pacotes** caixa de diálogo. Você pode adicionar individuais referências a assemblies de extensibilidade específicos ou adicionar o SDK do VS faz referência a assemblies de uma vez usando o SDK do VS [pacote Meta](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). Para saber mais sobre o NuGet, consulte o [NuGet documentação](http://docs.microsoft.com/NuGet) e [Package Manager UI](http://docs.microsoft.com/NuGet/Tools/Package-Manager-UI) tópicos.  
  
 Quando você usar as versões do NuGet dos assemblies de referência do SDK do VS, outro usuário não precisa instalar o SDK do VS para abrir e compilar o projeto.  Os assemblies de referência do NuGet e ferramentas de compilação do SDK do VS serão instaladas automaticamente em seu computador para o projeto.  
  
 Os modelos de item do SDK do VS usam NuGet para suas referências e ferramentas de compilação para que você obtenha os benefícios do NuGet por padrão.  
  
> [!NOTE]
>  Você pode continuar a usar os assemblies de referência do SDK do VS instalado com seus projetos (localizado em \<local de instalação do Visual Studio > \ VSSDK\VisualStudioIntegration\Common\Assemblies) e projetos de extensibilidade existentes não precisam ser atualizado para usar os pacotes do NuGet.  O projeto **referencia / adicionar referência** diálogo continua a usar os assemblies de referência do SDK do VS instalado.  
>   
>  Se você quiser modificar seus projetos existentes para usar o NuGet, consulte [como: VSPackages migrar para o Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) que tem uma seção sobre como atualizar projetos de extensibilidade para pacotes do NuGet.  
  
## <a name="light-bulbs"></a>Lâmpadas  
 Uma das maneiras mais interessantes novo de escrever código de extensão é fornecida pelo projeto Roslyn. Para obter mais informações, consulte [Roslyn](https://github.com/dotnet/Roslyn).  
  
 Lâmpadas são um novo recurso que acompanha o VSSDK. Eles são os ícones usados no editor do Visual Studio que se expandem para exibir um conjunto de ações de refatoração do código ou correções para problemas identificados pelos analisadores de código internos. Para obter mais informações, consulte [passo a passo: exibindo sugestões de lâmpada](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
## <a name="updated-user-experience-guidelines"></a>Diretrizes de experiência do usuário atualizado  
 Criando novas extensões ou recursos para o Visual Studio? Check-out atualizado e expandido [diretrizes de experiência de usuário do Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Você encontrará o [tokens de cores](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [tamanhos de fonte](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [especificações de layout da caixa de diálogo](../extensibility/ux-guidelines/layout-for-visual-studio.md)e outras orientações que você precisa integrar perfeitamente a nova interface do usuário com o Visual Studio.