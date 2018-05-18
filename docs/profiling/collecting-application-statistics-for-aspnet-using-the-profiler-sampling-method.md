---
title: Coletar estatísticas para aplicativos Web ASP.NET | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, sampling method
- sampling profling method
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 9be304398fcefaf6a38ca7e1d557f2c9146b4872
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/11/2018
---
# <a name="collect-statistics-for-aspnet-web-apps"></a>Coletar estatísticas para aplicativos Web ASP.NET

Esta seção descreve os procedimentos e as opções para coletar estatísticas de desempenho de um aplicativo Web ASP .NET usando a ferramenta de linha de comando **VSPerfASPNETCmd** e **VSPerfCmd** e o método de criação de perfil de amostragem.  
  
> [!NOTE]
>  Os recursos de segurança aprimorados no Windows 8 e no Windows Server 2012 exigiram alterações significativas na maneira como o criador de perfil do Visual Studio coleta dados nessas plataformas. Os aplicativos UWP também requerem novas técnicas de coleta. Consulte [Ferramentas de desempenho em aplicativos do Windows 8 e do Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Embora a ferramenta **VSPerfCmd** forneça acesso completo à funcionalidade de Ferramentas de Criação de Perfil, inclusive pausar e retomar a criação de perfil e coletar outros dados do processador e de contadores de desempenho do Windows, você deverá usar a ferramenta de linha de comando **VSPerfASPNETCmd** quando não precisar dessa funcionalidade. A ferramenta de linha de comando **VSPerfASPNETCmd** é o método de preferência quando você está criando o perfil de sites da Web ASP.NET usando o criador de perfil autônomo. Em comparação com a ferramenta de linha de comando [VSPerfCmd](../profiling/vsperfcmd.md), nenhuma variável de ambiente precisa ser definida nem é necessário reiniciar o computador. Para obter mais informações, consulte [Criação de perfil do site rápida com VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## <a name="common-tasks"></a>Tarefas comuns  
  
|Tarefa|Conteúdo relacionado|  
|----------|---------------------|  
|**Attach the profiler to an ASP.NET application (Anexar o criado de perfil a um aplicativo ASP.NET)**|-   [How to: Attach the Profiler to an ASP.NET Web Application to Collect Application Statistics (Como anexar o criador de perfil a um aplicativo Web ASP .NET para coletar estatísticas do aplicativo)](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Tarefas relacionadas  
  
### <a name="profiling-aspnet-web-applications"></a>Criando perfil de aplicativos Web do ASP.NET  
  
|Tarefa|Conteúdo relacionado|  
|----------|---------------------|  
|**Criar perfil usando o método de instrumentação**|-   [Coletando dados de tempo detalhados usando a instrumentação](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|  
|**Profile memory allocation and garbage collection (Alocação de memória de perfil e coleta de lixo)**|-   [Coletando dados de memória](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|  
|**Criar perfil de contenção de recursos e atividade de thread**|-   [Coletando dados de simultaneidade](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|  
  
### <a name="sampling-method"></a>Método de Amostragem  
  
|Tarefa|Conteúdo relacionado|  
|----------|---------------------|  
|**Criar o perfil de aplicativos autônomos (clientes)**|-   [Coletando estatísticas do aplicativo usando amostragem](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|  
|-   **Profile services (Serviços de perfil)**|-   [Coletando estatísticas do aplicativo usando amostragem](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>Analisando exibições e relatórios dos dados de amostragem  
 [Exibições de dados do método de amostragem](../profiling/profiler-sampling-method-data-views.md)