---
title: Relatório de ETW (Rastreamento de Eventos para Windows) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49ea37f6830c7e4fdf8c8d94b0f323c6337329c5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475530"
---
# <a name="event-tracing-for-windows-etw-report"></a>Relatório de Rastreamento de Eventos para Windows (ETW)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [Event Tracing for Windows (ETW) relatório](https://docs.microsoft.com/visualstudio/profiling/event-tracing-for-windows-etw-report).  
  
O Relatório de ETW (Rastreamento de Eventos para Windows) lista os eventos ETW que são registrados em uma sessão de desempenho das Ferramentas de Criação de Perfil [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Dados de ETW são coletados em um arquivo binário (.etl).  
  
> [!NOTE]
>  Não é possível exibir relatórios ETW na interface [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
-   Para obter informações sobre como coletar dados ETW usando as Ferramentas de Criação de Perfil na interface [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], consulte [Como coletar dados ETW (Rastreamento de Eventos para Windows)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
-   Para obter informações sobre como coletar dados ETW usando as ferramentas de linha de comando [VSPerfCmd](../profiling/vsperfcmd.md), consulte [Eventos](../profiling/events-vsperfcmd.md).  
  
-   O relatório de ETW é gerado usando o comando **VSReport/Summary:ETW**. Para obter mais informações, confira [VSPerfReport](../profiling/vsperfreport.md).  
  
|Column|Descrição|  
|------------|-----------------|  
|**Carimbo de data/hora**|Identifica quando o evento ocorreu.|  
|**ID do Processo**|Identifica o processo que gerou o evento.|  
|**ID do Thread**|Identifica o thread que gerou o evento.|  
|**Descrição**|Identifica o provedor de eventos.|  
|**Tipo**|Identifica o tipo de evento.|  
|**Propriedades**|As propriedades do evento. Cada evento é um par nome-valor separado por vírgulas e limitado entre colchetes.|



