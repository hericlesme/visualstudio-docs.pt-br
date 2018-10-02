---
title: Tempo de preempção | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 614b049bf7aa881ce4454d8f832190b0391ff342
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474615"
---
# <a name="preemption-time"></a>Tempo de preempção
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [tempo de preempção](https://docs.microsoft.com/visualstudio/profiling/preemption-time).  
  
Esses segmentos na linha do tempo estão associados os tempos de bloqueio categorizados como Preempção. Esta categoria implica que um thread é alternado devido a um destes motivos:  
  
-   O agendador substituiu usando um thread de prioridade mais alta.  
  
-   O quantum de execução do thread expirou e outros threads estavam prontos para execução.  
  
 Durante esse tempo, um thread foi bloqueado por uma espera de kernel, motivo pelo qual a visualização simultânea está contando como preempção. Segmentos de preempção iniciam quando um thread é empurrado para fora de um núcleo lógico e terminam quando esse thread continua a execução.  
  
 A dica de ferramenta para um segmento que admitiu preempção exibe o nome do processo ou thread que causou a preempção. No entanto, isso não significa que o processo ou thread que assumiu o controle foi realmente executado durante o período de admitiu preempção.  
  
## <a name="see-also"></a>Consulte também  
 [Exibição de Threads](../profiling/threads-view-parallel-performance.md)



