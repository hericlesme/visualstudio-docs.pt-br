---
title: Coletando estatísticas de aplicativo para aplicativos autônomos usando a linha de comando do criador de perfil | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 951c65672f3b5aa6bb9555ace4622cfb60b04fc6
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34263685"
---
# <a name="collect-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Coletar estatísticas de aplicativo para aplicativos autônomos usando a linha de comando do criador de perfil
Esta seção descreve os procedimentos e as opções para coletar estatísticas de desempenho para um aplicativo cliente (autônomo) usando o método de amostragem da linha de comando.  
  
> [!NOTE]
>  Os recursos de segurança aprimorados no Windows 8 e no Windows Server 2012 exigiram alterações significativas na maneira como o criador de perfil do Visual Studio coleta dados nessas plataformas. Os aplicativos UWP também requerem novas técnicas de coleta. Consulte [Ferramentas de desempenho em aplicativos do Windows 8 e do Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Tarefas comuns  
  
|Tarefa|Conteúdo relacionado|  
|----------|---------------------|  
|**Start an application by using profiling (Iniciar um aplicativo usando a criação de perfil)**|-   [Como iniciar um aplicativo autônomo e coletar estatísticas do aplicativo](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Attach the profiler to a running .NET Framework application (Anexar o criador de perfil a um aplicativo do .NET Framework em execução)**|-   [Como anexar o criador de perfil a um aplicativo do .NET Framework e coletar estatísticas do aplicativo](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)|  
|**Attach the profiler to a running C/C++ application (Anexar o criador de perfil a um aplicativo C/C++ em execução)**|-   [Como anexar o criador de perfil a um aplicativo nativo e coletar estatísticas do aplicativo](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Add tier-interaction data (Adicionar dados de interação de camada)**|-   [Coletando dados de interação entre camadas](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>Tarefas relacionadas  
  
### <a name="profile-stand-alone-applications"></a>Criar perfil de aplicativos autônomos  
  
|Tarefa|Conteúdo relacionado|  
|----------|---------------------|  
|**Instrument an application (Instrumentar um aplicativo)**|-   [Coletar dados de tempo detalhados usando a instrumentação](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|  
|**Collect .NET memory allocation and garbage collection data (Coletar dados de alocação de memória e de coleta de lixo do .NET)**|-   [Coletar dados de memória do .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|  
|**Collect resource contention and thread execution data (Coletar dados de contenção de recursos e de execução do thread)**|-   [Coletar dados de simultaneidade](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|  
  
### <a name="profile-by-using-the-sampling-method"></a>Criar perfil usando o método de amostragem  
  
|Tarefa|Conteúdo relacionado|  
|----------|---------------------|  
|**Criar o perfil de aplicativos Web ASP.NET**|-   [Coletar estatísticas do aplicativo usando amostragem](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|  
|**Profile services (Serviços de perfil)**|-   [Coletar estatísticas do aplicativo usando amostragem](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md). Descreve como coletar estatísticas de desempenho de serviços Windows usando o método de amostragem.|  
  
### <a name="analyze-sampling-data-views-and-reports"></a>Analisar exibições e relatórios dos dados de amostragem  
 [Exibições de dados do método de amostragem](../profiling/profiler-sampling-method-data-views.md)

