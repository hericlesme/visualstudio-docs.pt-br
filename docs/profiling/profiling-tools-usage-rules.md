---
title: "Regras de uso das ferramentas de criação de perfil | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2660586ce2757f2aa1b58c6c7b0e4dc36a700bc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="profiling-tools-usage-rules"></a>Regras de uso das ferramentas de criação de perfil
As regras de desempenho na categoria de Uso de Ferramentas de Criação de Perfil fornecem diretrizes para usar o criador de perfil para coletar dados de forma mais eficiente.  
  
|||  
|-|-|  
|[DA0002: VSPerfCorProf.dll está ausente](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|A criação de perfil de linha de comando pode conter dados incompletos para binários [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Isso pode ser causado por não configurar variáveis de ambiente corretas.|  
|[DA0003: muitas amostras de kernel](../profiling/da0003-many-kernel-samples.md)|Muitas amostras de criação de perfil que ocorreram fora da execução do binário de destino foram registrados. Para coletar dados mais precisos, considere usar o método de instrumentação.|  
|[DA0004: uso elevado do processador](../profiling/da0004-high-processor-usage.md)|Os dados de criação de perfil sugerem que seus processadores estavam consistentemente ocupados durante a criação de perfil. Para coletar dados mais precisos, considere usar o método de amostragem.|  
|[DA0008: poucas amostras coletadas](../profiling/da0008-few-samples-collected.md)|O número de amostras coletados na criação de perfil não foi alto o suficiente para ser estatisticamente significativo. Considere realizar uma nova criação de perfil e executar o aplicativo por mais tempo. Considere também usar o método de instrumentação para coletar dados.|  
|[DA0026: processamento de tempo de CPU do kernel excessivo](../profiling/da0026-excessive-kernel-cpu-time-processing.md)|Uma parte significativa de tempo na criação de perfil ocorreu no modo de núcleo de kernel de processador. Considere a amostragem por meio de chamadas do sistema como a métrica em vez de usar o tempo como a métrica.|  
|[DA0029: versão do CLR sem suporte](../profiling/da0029-unsupported-clr-version.md)|O binário analisado está usando uma versão de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que não tem suporte no criador de perfil. Os relatórios do criador de perfil não podem resolver nomes de símbolos.|  
|[DA0030: coletar medições de interação de camada para projetos de banco de dados](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|Foi coletado um número significativo de chamadas para métodos no namespace <xref:System.Data?displayProperty=fullName>. Para incluir dados sobre as chamadas de banco de dados, considere coletar dados de interação entre camadas em execução de análise.|