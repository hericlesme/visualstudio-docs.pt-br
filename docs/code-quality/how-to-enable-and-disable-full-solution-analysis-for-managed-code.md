---
title: "Como: habilitar e desabilitar análise de solução completa para código gerenciado | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 64b541093aaf1a710976c0f53a3214b5d2a47e0d
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Como: habilitar e desabilitar análise de solução completa para código gerenciado

*Total de análise de solução* é um recurso do Visual Studio que permite que você veja somente em arquivos abertos de Visual c# ou Visual Basic em sua solução de problemas de análise do código ou também em código de arquivos que estão fechados. Por padrão, a análise de solução completa é habilitado para o Visual Basic e desabilitado para o Visual c#.

Embora seja útil visualizar todos os problemas em todos os arquivos, talvez seja confuso. Ele também pode lenta do Visual Studio para baixo se sua solução for muito grande ou tem muitos arquivos. Para limitar o número de saídas mostrado e melhorar o desempenho do Visual Studio, você pode desabilitar análise de solução completa. Você pode facilmente habilitar este recurso novamente se necessário.

## <a name="to-toggle-full-solution-analysis"></a>Para alternar a análise de solução completa

1. Para abrir o **opções** escolha a caixa de diálogo, na barra de menu do Visual Studio **ferramentas** > **opções**.

1. No **opções** caixa de diálogo caixa, escolha **Editor de texto** > **c#** ou **básica**  >   **Advanced**.

1. Selecione o **habilitar análise de solução completa** caixa de seleção para habilitar a análise de solução completa, ou desmarque a caixa para desativá-lo. Escolha o **Okey** botão quando terminar.

    ![Habilite a caixa de seleção de análise de solução completa. ] (../code-quality/media/fsa_toolsoptions.png "FSA_ToolsOptions")

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Resultados de habilitar e desabilitar análise de solução completa

Na captura de tela a seguir, você pode ver os resultados quando a análise de solução completa está habilitada. Todos os erros e problemas de análise de código em *todos os* dos arquivos na solução aparecem, independentemente se os arquivos estiverem abertos ou não.

![Análise de solução completa habilitado. ] (../code-quality/media/fsa_enabled.png "FSA_Enabled")

Captura de tela a seguir mostra os resultados da mesma solução depois de desabilitar análise de solução completa. Somente os erros e problemas de análise de código em abrem solução arquivos aparecem na lista de erros.

![Análise de solução completa desabilitado. ] (../code-quality/media/fsa_disabled.png "FSA_Disabled")

## <a name="automatically-disabling-full-solution-analysis"></a>Desabilitar automaticamente a análise de solução completa

Se o Visual Studio detectar que 200MB ou menos memória do sistema está disponível para ele, ele automaticamente desabilita a análise de solução completa (bem como alguns outros recursos) se ele está habilitado. Se isso ocorrer, um alerta será exibida informando sobre isso. Um botão permite habilitar novamente a análise de solução completa se desejado.

![Suspender a análise de solução completa de texto de alerta](../code-quality/media/fsa_alert.png "FSA_Alert")