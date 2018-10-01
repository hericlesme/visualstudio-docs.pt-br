---
title: Personalizando a página inicial para o Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: 48
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7bc8c27c98127bbbdfd7a1dddbab7124b8dc1d32
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47461467"
---
# <a name="customizing-the-start-page-for-visual-studio"></a>Personalizando a página inicial do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [personalizar a página inicial do Visual Studio](https://docs.microsoft.com/visualstudio/ide/customizing-the-start-page-for-visual-studio).  
  
É possível personalizar a página inicial do Visual Studio de várias maneiras padrão, mostrando, por exemplo, a caixa de diálogo **Abrir Projeto** ou abrindo a solução que foi carregada mais recentemente. Também é possível mostrar uma página inicial personalizada, que é uma página XAML do Windows Presentation Foundation (WPF) executada em uma janela de ferramenta e pode executar comandos que são internos do Visual Studio.  
  
## <a name="customizing-the-default-start-page"></a>Personalizando a página inicial padrão  
  
1.  Na barra de menus, escolha **Ferramentas**, **Opções**.  
  
2.  Expanda **Ambiente** e escolha **Inicialização**.  
  
3.  Na lista **Na inicialização**, escolha o item da personalização desejado.  
  
## <a name="show-a-custom-start-page"></a>Mostrar uma página inicial personalizado  
  
1.  Instale uma página inicial personalizada de uma das seguintes maneiras:  
  
    -   Instale-a por meio da [Galeria do Visual Studio](http://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=start%20page), de outro site ou de uma página da intranet local.  
  
        > [!NOTE]
        >  Se desejar uma página que é direcionada para uma versão anterior do Visual Studio, você pode atualizá-la usando o SDK do Visual Studio. Ver [como: atualizar uma página de início personalizados do Visual Studio](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).  
  
         Abrir um arquivo. VSIX que contém uma página inicial personalizada, ou copie e cole os arquivos de página inicial para o **% USERPROFILE % Documents\Visual Studio 2015\StartPages** pasta em seu computador.  
  
    -   Criar sua própria página inicial se você instalou o SDK do Visual Studio.  
  
         Ver [criar a sua própria página inicial](../misc/creating-your-own-start-page.md).  
  
2.  Na barra de menus, escolha **Ferramentas**, **Opções**.  
  
3.  Expanda **Ambiente** e escolha **Inicialização**.  
  
4.  Na lista **Personalizar Página Inicial**, escolha a página desejada.  
  
> [!NOTE]
>  Se um erro em uma página inicial personalizada causar pane no Visual Studio, você poderá iniciar o Visual Studio no modo de segurança e defini-lo para usar a página inicial padrão. Consulte [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).  
  
## <a name="see-also"></a>Consulte também  
 [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Criando sua própria página inicial](../misc/creating-your-own-start-page.md)



