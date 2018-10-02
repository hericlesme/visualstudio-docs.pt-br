---
title: Tempo de E-S (Exibição de Threads) | Microsoft Docs
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
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d25512da43fc32b42c2a1f79e3c8dbe992ea30ce
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475449"
---
# <a name="io-time-threads-view"></a>Tempo de E/S (exibição de threads)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [e / S de tempo (exibição Threads)](https://docs.microsoft.com/visualstudio/profiling/i-o-time-threads-view).  
  
Esses segmentos na linha do tempo estão associados aos tempos de bloqueio categorizados como E/S. Isso significa que um thread está aguardando uma operação de E/S ser concluída. O thread pode ter sido bloqueado em uma API ou por uma espera de kernel relacionado ao Visualizador de Simultaneidade que está contando como E/S. APIs como `CreateFile()`, `ReadFile()` e `WSARecv()` pertencem a esse grupo.  
  
## <a name="see-also"></a>Consulte também  
 [Exibição de Threads](../profiling/threads-view-parallel-performance.md)



