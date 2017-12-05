---
title: Otimizar o desempenho do Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing performance [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.performancecenter
ms.technology: vs-ide-general
ms.openlocfilehash: d1058ca5762db28f0afc678a9d31cc6f0f3be6bc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="optimize-visual-studio-performance"></a>Otimizar o desempenho do Visual Studio
O Visual Studio foi projetado para iniciar da forma mais rápida e eficiente possível. No entanto, determinadas extensões e janelas de ferramentas do Visual Studio poderão afetar negativamente o tempo de inicialização quando forem carregadas. Você pode controlar o comportamento das extensões e das janelas de ferramentas lentas na caixa de diálogo **Gerenciar o Desempenho do Visual Studio**. Para ver mais dicas gerais sobre como melhorar o desempenho, consulte [Dicas e truques de desempenho do Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md).  

## <a name="startup-behavior"></a>Comportamento da inicialização

Para evitar estender o tempo de inicialização, o Visual Studio 2017 carrega extensões usando uma abordagem _sob demanda_. Esse comportamento significa que as extensões não abrem imediatamente após o Visual Studio ser iniciado, mas conforme necessário. Além disso, como as janelas de ferramentas deixadas abertas em uma sessão anterior do Visual Studio podem deixar o tempo de inicialização lento, o Visual Studio abre as janelas de ferramentas de uma maneira mais inteligente para evitar afetar o tempo de inicialização.  

Se o Visual Studio detectar lentidão na inicialização, uma mensagem pop-up será exibida, alertando-o para a janela de ferramentas ou extensão que está causando a lentidão. A mensagem fornece um link para a caixa de diálogo **Gerenciar o Desempenho do Visual Studio**. Você também pode acessar essa caixa de diálogo escolhendo **Ajuda**, **Gerenciar o Desempenho do Visual Studio** na barra de menus.  

![Gerenciar o Desempenho do Visual Studio – pop-up indicando "Observamos que a extensão ... está deixando o Visual Studio mais lento"](../ide/media/vside_perfdialog_popup.png)

A caixa de diálogo lista as janelas de ferramentas e extensões que estão afetando o desempenho de inicialização. Você pode alterar as configurações das janelas de ferramentas e das extensões para melhorar o desempenho de inicialização.  

## <a name="to-change-extension-settings-to-improve-startup-solution-load-and-typing-performance"></a>Para alterar as configurações das extensões para melhorar o desempenho da inicialização, do carregamento de soluções e da digitação

1. Abra a caixa de diálogo **Gerenciar o Desempenho do Visual Studio** escolhendo **Ajuda**, **Gerenciar o Desempenho do Visual Studio** na barra de menus.  

    Se uma extensão estiver retardando a inicialização, o carregamento de soluções ou a digitação no Visual Studio, a extensão aparecerá na caixa de diálogo **Gerenciar o Desempenho do Visual Studio** em **Extensões**, **Inicialização** (ou **Carregamento da Solução** ou **Digitação**).  

    ![Gerenciar o Desempenho do Visual Studio – exibição de extensões](../ide/media/vside_perfdialog_extensions.png)

2. Escolha a extensão que você deseja desabilitar e clique no botão **Desabilitar**.  

Você pode sempre habilitar novamente a extensão para sessões futuras usando o Gerenciador de Extensões ou a caixa de diálogo Gerenciar o Desempenho do Visual Studio.

## <a name="to-change-tool-window-settings-to-improve-startup-time"></a>Para alterar as configurações das janelas de ferramentas para melhorar o tempo de inicialização

1. Abra a caixa de diálogo **Gerenciar o Desempenho do Visual Studio** escolhendo **Ajuda**, **Gerenciar o Desempenho do Visual Studio** na barra de menus.  

    Se uma janela de ferramentas estiver retardando a inicialização do Visual Studio, ela será exibida na caixa de diálogo **Gerenciar o Desempenho do Visual Studio** em **Janelas de Ferramentas**, **Inicialização**.  

2. Escolha a janela de ferramentas da qual você deseja alterar o comportamento.  

3. Escolha uma das seguintes três opções:    

    - **Usar comportamento padrão:** o comportamento padrão da janela de ferramentas. Manter essa opção selecionada não melhorará o desempenho de inicialização.  

    - **Não mostrar janela na inicialização:** a janela de ferramentas especificada sempre estará fechada ao abrir o Visual Studio, mesmo se ela for deixada aberta em uma sessão anterior. Você pode abrir a janela de ferramentas no menu apropriado quando necessário.  
    
    - **Ocultar automaticamente janela na inicialização:** se uma janela de ferramentas tiver sido deixada aberta em uma sessão anterior, essa opção recolherá o grupo da janela de ferramentas na inicialização para evitar inicializar a janela de ferramentas. Essa opção é uma boa alternativa se você usa uma janela de ferramentas com frequência. A janela de ferramentas ainda está disponível, mas não afeta mais negativamente o tempo de inicialização do Visual Studio.  

    ![Gerenciar o Desempenho do Visual Studio – exibição da janela de ferramentas](../ide/media/vside_perfdialog_toolwindows.png)

## <a name="speed_up_solution_load"></a>Carregar grandes soluções mais rapidamente no Visual Studio 2017

O Visual Studio 2017 introduz um novo recurso chamado carga de solução leve, que reduz o tempo e a memória necessários para carregar soluções grandes no IDE. Se você tiver uma solução grande que contém muitos projetos C#, VB ou C++, provavelmente observará um benefício significativo do desempenho se habilitar a carga de solução leve. Para saber mais detalhadas sobre como você pode se beneficiar usando esse recurso, confira [Otimizar o carregamento de solução](../ide/optimize-solution-loading-in-visual-studio.md).

### <a name="enable-or-disable-lightweight-solution-load"></a>Habilitar ou desabilitar a carga de solução leve

Você pode clicar com o botão direito do mouse no nome da solução no Gerenciador de Soluções e selecionar **Habilitar a Carga de Solução Leve**. Depois de selecionar a opção, você precisa fechar e reabrir a solução para ativar a carga de solução leve.

![Gerenciador de Soluções](../ide/media/VSIDE_LSL_Solution_Setting.png)

Para definir as configurações globais para carga de solução leve, confira [Otimizar o carregamento de solução](../ide/optimize-solution-loading-in-visual-studio.md#global_solution_load_settings).

## <a name="see-also"></a>Consulte também
[Dicas e truques de desempenho do Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md)
