---
title: Começando a desenvolver extensões do Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 09/18/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 44403b5d60fc13666ffc6ec00558b80ef3a50ea9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144457"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Começando a desenvolver extensões do Visual Studio
Se você nunca escreveu uma extensão do Visual Studio antes, você provavelmente terá algumas perguntas. São listados algumas das mais comuns aqui. Se você não vir as informações que você está procurando, use os botões de comentários (**esta página foi útil?** na parte inferior da tela) para solicitar que você deseja.  
  
## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>O software necessário desenvolver extensões do Visual Studio?  
 Você precisa instalar o SDK do Visual Studio além do Visual Studio para desenvolver extensões do Visual Studio. Você pode instalar o SDK do Visual Studio como parte da instalação regular ou você pode instalá-lo mais tarde. Para obter mais informações sobre como instalar o SDK do Visual Studio, consulte [SDK do Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Que tipos de coisas pode fazer com extensões do Visual Studio?  
 O sky's o limite quando se trata de imaginando diferentes extensões do Visual Studio. Obviamente, a maioria das extensões tem algo a ver com a escrita de código, mas que não precisa ser o caso. Aqui estão alguns exemplos dos tipos de extensões, que você pode criar:  
  
-   Suporte para idiomas que não estão incluídos no Visual Studio, com cores de sintaxe, IntelliSense e suporte de compilador e de depuração  
  
-   As ferramentas de produtividade que ampliam o núcleo IDE experiência com modelos adicionais, caixas de diálogo refatoração, novo código ou janelas de ferramentas  
  
-   Designers de domínio específico para cenários como o suporte de design ou na nuvem de dados  
  
 Para obter exemplos de extensões, confira o [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Muitas extensões estão abertas originar e o Marketplace inclui links para seu repositório GitHub. 
  
## <a name="which-visual-studio-features-can-i-extend"></a>Quais recursos do Visual Studio pode estender?  
 Em teoria, você pode estender qualquer parte do Visual Studio: menus, barras de ferramentas, comandos, windows, soluções, projetos, editores e assim por diante.  
  
 Na prática, descobrimos que os recursos que a maioria das pessoas que desejam estender são comandos, menus e barras de ferramentas, windows, IntelliSense e projetos. Aqui estão os links para as seções relevantes:  
  
-   [Estendendo os Menus e comandos](../extensibility/extending-menus-and-commands.md): adicionar seus próprios itens de menus do Visual Studio e barras de ferramentas. Você pode usá-los para iniciar a nova funcionalidade do Visual Studio ou seus próprios aplicativos de ajuda externo. Você também pode fornecer atalhos personalizados para os itens de menu.  
  
-   [Estender e personalizar janelas de ferramenta](../extensibility/extending-and-customizing-tool-windows.md): estender as janelas de ferramentas existente ou criar suas próprias janelas de ferramenta. Por exemplo, você pode adicionar novas propriedades para o **propriedades**, ou você pode criar uma nova janela de ferramenta para adicionar recursos adicionais.  
  
-   [Editor e extensões de serviço de linguagem](../extensibility/editor-and-language-service-extensions.md): adicione suas personalizações o IntelliSense fornecida para idiomas do Visual Studio ou crie o suporte para novas linguagens de programação. Você pode criar um novo conclusões, sugestões e dicas de ferramenta do novo Inforapida. Com lâmpadas, você pode adicionar refatoração sugestões e correções de código para oferecer suporte a novas linguagens de programação.  
  
-   [Estender projetos](../extensibility/extending-projects.md)  
  
-   [Estender opções e configurações de usuário](../extensibility/extending-user-settings-and-options.md)  
  
-   [Estender propriedades e a janela de propriedades](../extensibility/extending-properties-and-the-property-window.md)  
  
-   [Estender outras partes do Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
  
-   [Shell isolado do Visual Studio](../extensibility/visual-studio-isolated-shell.md)  
  
##  <a name="BKMK_ProjectTemplate"></a> Quais modelos de projeto são fornecidos pelo VSSDK?  
 Os dois tipos principais de extensões são extensões VSPackages e MEF. Em geral, VSPackage extensões são usadas para extensões de usarem ou estendem a comandos, janelas de ferramentas e projetos. Extensões MEF são usadas para estender ou personalizar o editor do Visual Studio.  
  
 Para extensões do Visual c# e Visual Basic, o VSSDK fornece um modelo de projeto VSIX vazio que pode ser usado junto com os novos modelos de item que criam comandos de menu, janelas de ferramentas e extensões do editor. Você também pode usar este modelo para modelos de projeto de pacote, trechos de código e outros artefatos para distribuição a outros usuários.  
  
 Para C++, o Assistente de VSPackage fornece o código para adicionar comandos de menu, janelas de ferramentas e editores personalizados.  
  
 O modelo de Shell isolado é usado para empacotar uma extensão em uma versão do shell do Visual Studio que você pode colocar a marca e distribuir como seu próprio. Os tópicos a seguir mostram como começar com cada tipo de extensão:  
  
-   Comandos de menu: [criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   Janelas de ferramentas: [criando uma extensão com uma janela de ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   Extensões do Editor: [criando uma extensão com um modelo de Item Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   VSPackages básico: [criando uma extensão com um VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
-   Modelo de projeto do VSIX: [guia de Introdução com o modelo de projeto do VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)  
  
-   Visual Studio isolated shell: [passo a passo: Criando um aplicativo de Shell isolado básico](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Como obter a extensão do my parecido com o Visual Studio?  
 Obter ótimas dicas para projetar a interface do usuário para a extensão no [diretrizes de experiência de usuário do Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="where-can-i-find-examples-of-vssdk-code"></a>Onde posso encontrar exemplos de código VSSDK?  
 Cada um dos links listados na seção anterior ter orientações passo a passo que mostram como implementar recursos específicos. Você também pode encontrar código-fonte aberto exemplos VSSDK no GitHub em [exemplos do Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples).  
  
## <a name="how-can-i-distribute-my-extension"></a>Como distribuir o extensão do my?  
 Você pode instalar a extensão em outro computador ou enviá-lo para seus amigos como um arquivo de .vsix, que você instalar clicando duas vezes nele. Você pode encontrar mais informações sobre pacotes VSIX no [envio extensões do Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 Você também pode publicar sua extensão no Visual Studio Marketplace, que é visível para um grande número de clientes do Visual Studio. Para obter um exemplo de uma extensão para o Marketplace de empacotamento, consulte [passo a passo: publicando uma extensão do Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Para obter mais informações sobre o que você precisa fazer para publicar no Marketplace, consulte [produtos e extensões para o Visual Studio](/vsts/integrate/ide/extensions/overview).
