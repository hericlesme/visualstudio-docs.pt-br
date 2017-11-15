---
title: "Personalizar a página inicial do Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 02/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
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
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 178c20c9c4c3af8f5252e70ca603cdf8f8335e52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="customize-the-start-page-for-visual-studio"></a>Personalizar a página inicial do Visual Studio
É possível personalizar a página inicial do Visual Studio de várias maneiras padrão, mostrando, por exemplo, a caixa de diálogo **Abrir Projeto** ou abrindo a solução que foi carregada mais recentemente. Também é possível mostrar uma página inicial personalizada, que é uma página XAML do Windows Presentation Foundation (WPF) executada em uma janela de ferramenta e pode executar comandos que são internos do Visual Studio.  

## <a name="customize-the-default-start-page"></a>Personalizar a página inicial padrão  

1.  Na barra de menus, escolha **Ferramentas**, **Opções**.  

2.  Expanda **Ambiente** e escolha **Inicialização**.  

3.  Na lista **Na inicialização**, escolha o item da personalização desejado.  

## <a name="show-a-custom-start-page"></a>Mostrar uma página inicial personalizado  

1.  Instale uma página inicial personalizada de uma das seguintes maneiras:  

    -   Instale-a por meio da [Galeria do Visual Studio](http://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=start%20page), de outro site ou de uma página da intranet local.  

        Abra um arquivo .vsix que contém uma página inicial personalizada ou copie e cole os arquivos de página inicial na pasta **%USERPROFILE% \My Documents\Visual Studio 2017\StartPages** do computador.  

    -   Criar sua própria página inicial se você instalou o SDK do Visual Studio.  

         Consulte [Criando uma página inicial personalizada](../extensibility/creating-a-custom-start-page.md).  

2.  Na barra de menus, escolha **Ferramentas**, **Opções**.  

3.  Expanda **Ambiente** e escolha **Inicialização**.  

4.  Na lista **Personalizar Página Inicial**, escolha a página desejada.  

> [!NOTE]
>  Se um erro em uma página inicial personalizada causar pane no Visual Studio, você poderá iniciar o Visual Studio no modo de segurança e defini-lo para usar a página inicial padrão. Consulte [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).  

## <a name="see-also"></a>Consulte também  
 [Personalizar o IDE do Visual Studio](../ide/personalizing-the-visual-studio-ide.md)   
