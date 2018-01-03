---
title: "Novidades na criação de perfil | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling
- what's new
ms.assetid: d4736cc8-8961-4089-be9e-d5190ce8353c
caps.latest.revision: "42"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8529bc4cc9708ea58a0480d61327c50c96c996fc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="whats-new-in-profiling-tools-in-includevsdev15miscincludesvsdev15mdmd"></a>Novidades nas Ferramentas de Criação de Perfil do [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]
As Ferramentas de Diagnóstico incluem novas visualizações para ajudar você a identificar problemas em seu aplicativo que precisam de correção. As Ferramentas de Diagnóstico agora incluem suporte para aplicativos ASP.NET.

Para obter informações adicionais, consulte as [Notas de Versão para [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#debuggingdiag).

Uma guia **Resumo** foi adicionada às ferramentas para ajudar você a focar áreas-chave da sua análise de desempenho. Essa guia mostra quantos eventos ocorreram, permite que você tire instantâneos do heap e que você habilite rapidamente a coleta de dados de uso da CPU. Essa exibição mostra qualquer evento do [Application Insights](https://azure.microsoft.com/en-us/documentation/articles/app-insights-visual-studio/) ou da [Análise da Interface do Usuário](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#UIAnalysis). Além disso, para o Visual Studio Enterprise, essa exibição também mostra eventos do IntelliTrace.

![Guia Resumo das Ferramentas de Diagnóstico](../profiling/media/DiagToolsSummaryTab-2.png "DiagToolsSummaryTab")

A ferramenta de uso da CPU tem [novas visualizações](../profiling/Beginners-Guide-to-Performance-Profiling.md) para ajudar você a identificar as funções que têm uma probabilidade maior de causar problemas de desempenho. A nova exibição **Chamador/Computador Chamado** permite a investigação dos custos de chamadas de função feitas de/para uma função selecionada.

![Exibição Chamador/Computador Chamado da Chamada das Ferramentas de Diagnóstico](../profiling/media/DiagToolsCallerCallee.png "DiagToolsCallerCallee")
  
## <a name="see-also"></a>Consulte também  
 [Criação de perfis no Visual Studio](../profiling/index.md)  
 [Tour pelos recursos de criação de perfil](../profiling/profiling-feature-tour.md)