---
title: SDK do Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3b6b75deb576e5cb4e23975e80428433fbbc143a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="visual-studio-sdk"></a>SDK do Visual Studio
O SDK do Visual Studio ajuda você a ampliar os recursos do Visual Studio ou integrar novos recursos do Visual Studio. Você pode distribuir suas extensões a outros usuários, bem como para o Visual Studio Marketplace. A seguir está algumas das maneiras em que você pode estender o Visual Studio:  
  
-   Adicionar comandos, botões, menus e outros elementos de interface do usuário para o IDE  
  
-   Adicionar janelas de ferramenta para a nova funcionalidade  
  
-   Estender o IntelliSense para um determinado idioma ou fornecem IntelliSense para novas linguagens de programação  
  
-   Use lâmpadas para fornecer dicas e sugestões para ajudam os desenvolvedores a escrever código melhor  
  
-   Habilitar o suporte para um novo idioma  
  
-   Adicionar um tipo de projeto personalizados  
  
-   Alcançar milhões de desenvolvedores por meio do Visual Studio Marketplace  
  
 Se você nunca escreveu uma extensão do Visual Studio antes, você deve encontrar mais informações sobre esses recursos e [começando a desenvolver extensões do Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>Instalar o SDK do Visual Studio  
 O SDK do Visual Studio é um recurso opcional na instalação do Visual Studio. Você também pode instalar o SDK do VS posteriormente. Para obter mais informações, consulte [instalar o SDK do Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Novidades no SDK do Visual Studio de 2017  
 O SDK do Visual Studio tem alguns recursos novos, como o formato do VSIX v3, bem como alterações que podem exigir que você atualize sua extensão de quebra. Para obter mais informações, consulte [Novidades no SDK do Visual Studio 2017](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Diretrizes de experiência de usuário do Visual Studio  
 Obter ótimas dicas para projetar a interface do usuário para a extensão no [diretrizes de experiência de usuário do Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 Você também pode aprender a fazer sua extensão de aparência excelente em dispositivos DPI alto com nosso [abordar problemas de DPI](../extensibility/addressing-dpi-issues2.md) tópico.  
  
 Aproveitar o [serviço de imagem e catálogo](../extensibility/image-service-and-catalog.md) para gerenciamento de imagem grande e suporte a alto DPI e temas.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Localizar e instalar extensões do Visual Studio existentes  
 Você pode encontrar as extensões do Visual Studio no **extensões e atualizações** caixa de diálogo no **ferramentas** menu. Para obter mais informações, consulte [Localizando e usando extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Você também pode encontrar extensões no [Visual Studio Marketplace](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Referência SDK do Visual Studio  
 Você pode encontrar a referência de API do SDK do Visual Studio em [referência de SDK do Visual Studio](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Amostras do Visual Studio SDK  
 Você pode encontrar exemplos de código aberto de extensões do SDK do VS no GitHub em [exemplos do Visual Studio](https://aka.ms/vs2015sdksamples). Este repositório GitHub contém exemplos que ilustram diversos recursos extensíveis no Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Outros recursos SDK do Visual Studio  
 Se você tiver dúvidas sobre o VSSDK ou compartilhar suas experiências desenvolver extensões, você pode usar o [Fórum de extensibilidade do Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) ou [ExtendVS Gitter Chatroom](https://gitter.im/Microsoft/extendvs).  
  
 Você pode encontrar mais informações no [Arcana VSX blog](http://blogs.msdn.com/b/vsx/) e uma série de blogs gravados pelo Microsoft MVPs:  
  
-   [Extensões do Visual Studio Favoritos](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Extensibilidade do Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Extensão do Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Consulte também  
 [Criando uma extensão com um comando de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Como: migrar projetos de extensibilidade para o Visual Studio de 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)   
 [Perguntas Frequentes: Convertendo suplementos para extensões de VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Gerenciamento de vários Threads em código gerenciado](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Comandos e Menus estendendo](../extensibility/extending-menus-and-commands.md)   
 [Adicionando comandos em barras de ferramentas](../extensibility/adding-commands-to-toolbars.md)   
 [Estender e personalizar as janelas de ferramentas](../extensibility/extending-and-customizing-tool-windows.md)   
 [Editor e extensões de serviço de linguagem](../extensibility/editor-and-language-service-extensions.md)   
 [Estendendo projetos](../extensibility/extending-projects.md)   
 [Opções e configurações de usuário de extensão](../extensibility/extending-user-settings-and-options.md)   
 [Criando modelos de Item e projeto personalizados](../extensibility/creating-custom-project-and-item-templates.md)   
 [Estendendo propriedades e a janela de propriedade](../extensibility/extending-properties-and-the-property-window.md)   
 [Estendendo a outras partes do Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Usando e fornecer serviços](../extensibility/using-and-providing-services.md)   
 [Gerenciando VSPackages](../extensibility/managing-vspackages.md)   
 [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)   
 [Envio de extensões do Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [Dentro do Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Suporte para o SDK do Visual Studio](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Arquivo morto](../extensibility/archive.md)   
 [Referência do SDK do Visual Studio](../extensibility/visual-studio-sdk-reference.md)
