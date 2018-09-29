---
title: Como habilitar e desabilitar análise de código automática para código gerenciado
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3113143b07ccb6f765cd0cf1735b34be6e952c72
ms.sourcegitcommit: 6672a1e9d135d7e5cca3cceea07c6fe5a0871475
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47443539"
---
# <a name="how-to-enable-and-disable-automatic-code-analysis-for-managed-code"></a>Como: habilitar e desabilitar análise de código automática para código gerenciado

Você pode configurar a análise de código a ser executado após cada compilação de um projeto de código gerenciado. Você pode definir propriedades de análise para cada configuração de compilação de código diferente, por exemplo, debug e release.

## <a name="to-enable-or-disable-automatic-code-analysis"></a>Para habilitar ou desabilitar análise de código automática

1. Na **Gerenciador de soluções**, clique com botão direito no projeto e, em seguida, escolha **propriedades**.

1. Na caixa de diálogo Propriedades do projeto, escolha o **análise de código** guia.

1. Especifique o tipo de compilação na **Configuration** e a plataforma de destino na **plataforma**.

1. Para habilitar ou desabilitar a análise de código automática, marque ou desmarque a **habilitar a análise de código no Build** caixa de seleção.

> [!NOTE]
> O **habilitar a análise de código no Build** caixa de seleção afeta somente a análise de código estático. Ele não afeta [analisadores de código do Roslyn](roslyn-analyzers-overview.md), que sempre é executado em compilação se você instalou-los como um pacote do NuGet. Se você quiser limpar erros do analisador do **lista de erros**, você pode suprimir todas as violações atuais, escolhendo **analisar** > **executar análise de código e suprimir Active Directory Problemas** na barra de menus. Para obter mais informações, consulte [suprimir violações](use-roslyn-analyzers.md#suppress-violations).
