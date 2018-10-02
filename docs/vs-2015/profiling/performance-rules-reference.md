---
title: Referência das Regras de Desempenho | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8f96819c5d6f8e2be1c7f92e53ebbb29d075886
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47473613"
---
# <a name="performance-rules-reference"></a>Referência de regras de desempenho
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [referência de regras de desempenho](https://docs.microsoft.com/visualstudio/profiling/performance-rules-reference).  
  
As regras de desempenho das Ferramentas de Criação de Perfil fornecem avisos adicionais e informações sobre o desempenho do seu aplicativo. Regras de desempenho analisam os dados em uma execução de criação de perfil que é coletada das fontes, tal como Windows e contadores de desempenho do processador. Mensagens de regra aparecem na janela Saída de Erro do ambiente de desenvolvimento integrado do [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. As mensagens são listadas com um dos seguintes níveis de regra:  
  
|||  
|-|-|  
|**Erro**|Algumas regras geram mensagens de erro porque a maioria dos problemas de desempenho não são erros diretos. Uma mensagem de erro pode indicar uma falha ao coletar dados de criação de perfil.|  
|**Aviso**|Os avisos indicam uma área do aplicativo que pode ser uma fonte de problemas de desempenho em potencial ou que poderia se beneficiar com otimizações.|  
|**Informações**|Mensagens informativas indicam que a análise de uma condição de regra não atingiu o limite para gerar uma mensagem de erro ou que as informações na mensagem é útil, mas não representa um problema de desempenho.|  
  
## <a name="in-this-section"></a>Nesta seção  
 [Regras de desempenho por ID](../profiling/performance-rules-by-id.md)  
  
 As regras de desempenho de Ferramentas de Criação de Perfil são organizadas em quatro categorias:  
  
|||  
|-|-|  
|[Regras de desempenho de uso do .NET Framework](../profiling/dotnet-framework-usage-performance-rules.md)|Regras que ajudam a usar o .NET Framework com eficiência.|  
|[Regras de desempenho de memória e paginação](../profiling/memory-and-paging-performance-rules.md)|Regras que analisam a memória gerenciada e o comportamento de paginação de seu aplicativo.|  
|[Regras de uso das ferramentas de criação de perfil](../profiling/profiling-tools-usage-rules.md)|Regras que ajudam a usar as Ferramentas de Criação de Perfil com eficiência.|  
|[Regras de desempenho do monitoramento de recurso](../profiling/resource-monitoring-performance-rules.md)|Mensagens informativas sobre a utilização de processador e de memória em uma execução de criação de perfil.|



