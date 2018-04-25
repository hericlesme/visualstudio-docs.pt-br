---
title: Tempo de E-S (Exibição de Threads) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e50301149f844e0063deeb970e5bfb5bd46a55c1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="io-time-threads-view"></a>Tempo de E/S (exibição de threads)
Esses segmentos na linha do tempo estão associados aos tempos de bloqueio categorizados como E/S. Isso significa que um thread está aguardando uma operação de E/S ser concluída. O thread pode ter sido bloqueado em uma API ou por uma espera de kernel relacionado ao Visualizador de Simultaneidade que está contando como E/S. APIs como `CreateFile()`, `ReadFile()` e `WSARecv()` pertencem a esse grupo.  
  
## <a name="see-also"></a>Consulte também  
 [Exibição de Threads](../profiling/threads-view-parallel-performance.md)