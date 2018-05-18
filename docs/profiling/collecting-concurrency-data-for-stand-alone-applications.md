---
title: Coletando dados de simultaneidade para aplicativos autônomos usando a linha de comando do criador de perfil | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d50f99fd59406340b47463f8be16e16c552316af
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/11/2018
---
# <a name="collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Coletando dados de simultaneidade para aplicativos autônomos usando a linha de comando do criador de perfil
O método de simultaneidade das Ferramentas de Criação de Perfil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permite coletar dados de contenção de recursos e dados de atividade do thread que mostram a utilização da CPU, contenção e migração do thread, atrasos na sincronização, áreas de ES sobrepostas e outros eventos do sistema.  
  
## <a name="common-tasks"></a>Tarefas comuns  
  
|Tarefa|Conteúdo relacionado|  
|----------|---------------------|  
|**Start a .NET Framework application and profile concurrency data (Iniciar um aplicativo do .NET Framework e criar o perfil de dados de simultaneidade)**|-   [How to: Launch a .NET Framework Application to Collect Concurrency Data (Como iniciar um aplicativo do .NET Framework para coletar dados de simultaneidade)](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)|  
|**Start a C/C++ application and profile concurrency data (Iniciar um aplicativo C/C++ e criar o perfil de dados de simultaneidade)**|-   [How to: Launch a Native Application to Collect Concurrency Data (Como iniciar um aplicativo nativo para coletar dados de simultaneidade)](../profiling/how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Attach the profiler to a running .NET Framework application (Anexar o criador de perfil a um aplicativo do .NET Framework em execução)**|-   [How to: Attach the Profiler to a .NET Framework Application to Collect Concurrency Data (Como anexar o criador de perfil a um aplicativo do .NET Framework para coletar dados de simultaneidade)](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)|  
|**Attach the profiler to a running C/C++ application (Anexar o criador de perfil a um aplicativo C/C++ em execução)**|-   [How to: Attach the Profiler to a Native Application and Collect Concurrency Data (Como anexar o criador de perfil a um aplicativo nativo e coletar dados de simultaneidade)](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Tarefas relacionadas  
  
### <a name="profiling-stand-alone-applications"></a>Criando perfil de aplicativos autônomos  
  
|Tarefa|Conteúdo relacionado|  
|----------|---------------------|  
|**Criar perfil usando o método de amostragem**|-   [Coletando estatísticas do aplicativo usando amostragem](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|  
|**Criar perfil usando o método de instrumentação**|-   [Coletando dados de tempo detalhados usando a instrumentação](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|  
|**Profile .NET memory allocation and garbage collection (Criar o perfil de alocação de memória e coleta de lixo do .NET)**|-   [Coletando dados de memória do .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|  
|**Adding tier-interaction data (Adicionando dados de interação de camadas)**|-   [Coletando dados de interação entre camadas](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
### <a name="profiling-concurrency-issues"></a>Problemas de simultaneidade da criação de perfil  
  
|Tarefa|Conteúdo relacionado|  
|----------|---------------------|  
|**Aplicativos ASP.NET do perfil**|-   [Coletando dados de simultaneidade](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|  
|**Profile services (Serviços de perfil)**|-   [Coletando dados de simultaneidade](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-concurrency-data-views-and-reports"></a>Analisando modos de exibição e relatórios de Dados de Simultaneidade  
 [Exibições de dados da contenção de recurso](../profiling/resource-contention-data-views.md)  
  
 [Visualização Simultânea](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>Referência  
 [Referência de ferramentas de criação de perfil de linha de comando](../profiling/command-line-profiling-tools-reference.md)