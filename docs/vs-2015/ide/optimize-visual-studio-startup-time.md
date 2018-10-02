---
title: Otimizar o tempo de inicialização do Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing startup time [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c2c31a67ac019435c5131a1ab33600d26c76f32d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464181"
---
# <a name="optimize-visual-studio-startup-time"></a>Otimizar o tempo de inicialização do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Idealmente, o Visual Studio sempre deve iniciar o mais rápido possível. No entanto, extensões do Visual Studio e janelas de ferramentas abertas podem afetar o tempo de inicialização porque eles são carregados automaticamente na inicialização. A janela **Gerenciar o Desempenho do Visual Studio** permite que você não apenas veja quais extensões e recursos afetam o tempo de inicialização do Visual Studio, mas também permite que você determine o comportamento de carregamento para ter mais controle sobre quão rapidamente o Visual Studio é iniciado.

## <a name="control-startup-behavior"></a>Controlar o comportamento de inicialização

Para evitar a estender o tempo de inicialização, o Visual Studio "15" evita carregar extensões durante a inicialização, usando uma abordagem de carregamento sob demanda. Isso significa que as extensões não abrem imediatamente após o Visual Studio ser iniciado, mas abrem de forma assíncrona conforme o necessário após a inicialização. Além disso, como as janelas de ferramentas deixadas abertas em uma sessão anterior do Visual Studio podem deixar o tempo de inicialização lento, o Visual Studio abre as janelas de ferramentas de uma maneira mais inteligente para evitar afetar o tempo de inicialização.

Se o Visual Studio detectar lentidão na inicialização, uma mensagem pop-up será exibida, alertando-o para a janela de ferramentas ou extensão que está causando a lentidão. A mensagem também fornece um link para a caixa de diálogo **Gerenciar o Desempenho do Visual Studio**, que lista as extensões e janelas de ferramentas que estão afetando o desempenho de inicialização. Essa caixa de diálogo permite que você altere as configurações de janela de ferramentas e extensão para melhorar o desempenho de inicialização.

![Gerenciar o Desempenho do Visual Studio – pop-up](../ide/media/vside-perfdialog-popup.PNG "Gerenciar o Desempenho do Visual Studio – pop-up")

A caixa de diálogo **Gerenciar o Desempenho do Visual Studio** tem duas categorias: **Extensões** e **Janelas de Ferramentas**.

### <a name="control-extensions"></a>Controlar extensões
Se uma extensão estiver tornando a inicialização do Visual Studio lenta, a extensão aparecerá na caixa de diálogo **Gerenciar o Desempenho do Visual Studio** quando você escolher um dos tipos de extensão. Se o impacto no tempo de inicialização (que está listado na seção **Impacto**) estiver inaceitavelmente alto, você poderá optar por sempre desabilitar a extensão na inicialização escolhendo o botão **Desabilitar**. Você pode habilitar novamente a extensão para sessões futuras usando o Gerenciador de Extensões ou a caixa de diálogo Gerenciar o Desempenho do Visual Studio.

![Gerenciar o Desempenho do Visual Studio – extensões](../ide/media/vside-perfdialog-extensions.PNG "Gerenciar o Desempenho do Visual Studio – extensões")

Além das extensões de inicialização, você também pode desabilitar extensões que são carregadas quando as soluções são carregadas ou quando um usuário digita. Basta escolha o cenário para ver uma lista das extensões associadas.

### <a name="control-tool-windows"></a>Controlar as janelas de ferramentas
Se uma janela de ferramentas estiver tornando a inicialização do Visual Studio lenta, você poderá optar por deixá-la com seu comportamento padrão (não fornecendo nenhum benefício na velocidade de inicialização) ou pode substituir seu comportamento escolhendo um dos dois comportamentos:

- **Não mostrar janela na inicialização:** se você escolher essa opção, a janela de ferramentas especificada sempre estará fechada ao abrir o Visual Studio, mesmo se ala for deixada aberta em uma sessão anterior. Você pode abrir a janela de ferramentas no menu.
- **Ocultar automaticamente janela na inicialização:** se uma janela de ferramentas tiver sido deixada aberta em uma sessão anterior, escolher essa opção recolherá o grupo da janela de ferramentas na inicialização para evitar inicializar a janela de ferramentas. Essa é uma boa opção se você usar uma janela de ferramentas com frequência, pois a janela de ferramentas ainda estará disponível, mas não afetará negativamente o tempo de inicialização do Visual Studio.

![Gerenciar o Desempenho do Visual Studio – janelas de ferramentas](../ide/media/vside-perfdialog-toolwindows.PNG "Gerenciar o Desempenho do Visual Studio – janelas de ferramentas")

Se posteriormente você mudar de ideia, poderá reverter qualquer uma dessas opções na caixa de diálogo **Gerenciar o Desempenho do Visual Studio**. Para abrir a caixa de diálogo **Gerenciar o Desempenho do Visual Studio**, na barra de menus, escolha **Ajuda**, **Gerenciar o Desempenho do Visual Studio**.


