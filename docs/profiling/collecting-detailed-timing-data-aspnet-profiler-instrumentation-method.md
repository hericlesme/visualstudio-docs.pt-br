---
title: Coletando Dados de Tempo Detalhados para um Aplicativo Web ASP .NET Usando o Método de Instrumentação do Criador de Perfil da Linha de Comando | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 07789eba81dbe0cce46e5cf1a14decff92a6892f
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/11/2018
---
# <a name="collecting-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Coletando dados de tempo detalhados para um aplicativo Web do ASP.NET usando o método de instrumentação do criador de perfil a partir da linha de comando
Esta seção descreve os procedimentos e opções para coletar dados de desempenho detalhados para um aplicativo Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] usando a ferramenta **VSPerfCmd** da linha de comando e o método de instrumentação.  
  
> [!NOTE]
>  A ferramenta **VSPerfCmd** dá acesso completo à funcionalidade de Ferramentas de Criação de Perfil, inclusive pausar e retomar a criação de perfil e coletar dados adicionais do processador e de contadores de desempenho do Windows. Também é possível usar a ferramenta de linha de comando **VSPerfASPNETCmd** quando essa funcionalidade não for necessária. Em comparação com a ferramenta de linha de comando [VSPerfCmd](../profiling/vsperfcmd.md), nenhuma variável de ambiente precisa ser definida e não é necessário reinicializar o computador. Para obter mais informações, consulte [Criação de perfil do site rápida com VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## <a name="common-tasks"></a>Tarefas comuns  
  
|Tarefa|Conteúdo relacionado|  
|----------|---------------------|  
|**Criar perfil para binários compilados estatisticamente**|-   [Como Instrumentar um Aplicativo do ASP.NET Compilado Estaticamente e Coletar Dados de Tempo Detalhados](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)|  
|**Criar perfil para binários compilados dinamicamente**|-   [Como Instrumentar um Aplicativo do ASP.NET Compilado Dinamicamente e Coletar Dados de Tempo Detalhados](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)|  
  
## <a name="related-tasks"></a>Tarefas relacionadas  
  
### <a name="profiling-aspnet-web-applications"></a>Criando perfil de aplicativos Web do ASP.NET  
  
|Tarefa|Conteúdo relacionado|  
|----------|---------------------|  
|**Criar perfil usando o método de amostragem**|-   [Coletando estatísticas do aplicativo usando amostragem](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|  
|**Profile memory allocation and garbage collection (Alocação de memória de perfil e coleta de lixo)**|-   [Coletando dados de memória](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|  
|**Criar perfil de contenção de recursos e atividade de thread**|-   [Coletando dados de simultaneidade](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|  
  
### <a name="profiling-by-using-the-instrumentation-method"></a>Criação de perfil usando o método de instrumentação  
  
|Tarefa|Conteúdo relacionado|  
|----------|---------------------|  
|**Criar o perfil de aplicativos autônomos (clientes)**|-   [Coletando dados de tempo detalhados usando a instrumentação](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|  
|**Profile services (Serviços de perfil)**|-   [Coletando dados de tempo detalhados usando a instrumentação](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|  
  
### <a name="analyzing-instrumentation-data-views-and-reports"></a>Analisando modos de exibição e relatórios de dados de instrumentação  
 [Exibições de dados do método de instrumentação](../profiling/instrumentation-method-data-views.md)