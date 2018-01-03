---
title: "Tempo de execução (exibição de threads) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.execution
helpviewer_keywords: Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 91fda110b3bf73b59d7c9d7d8ff6f7226f9ec5fa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="execution-time-threads-view"></a>Tempo de execução (exibição de threads)
Esses segmentos na linha do tempo de exibição de threads representam o tempo de execução, quando o thread está ativamente trabalhando em um núcleo lógico no sistema.  
  
 As alterações no status de thread são detectadas por meio de eventos de alternância de contexto do kernel. o ETW (Rastreamento de Eventos para Windows) captura pilhas de amostra a cada milissegundo. Em um segmento verde muito curto, é possível que nenhuma amostra seja coletada. Portanto, alguns segmentos de execução curtos podem não mostrar nenhuma pilha de chamadas.  
  
 Quando você clica em um segmento de execução, a Visualização Simultânea exibe a pilha de amostra mais próxima do local do clique. O local da pilha de amostra é mostrado por uma seta preta ou pelo cursor do sistema, acima da linha do tempo e a pilha de amostra é exibida na guia **Atual**.  
  
 Para ver um perfil de amostragem tradicional para todos os segmentos de execução na exibição atual, clique em **Execução** no perfil de linha de tempo visível.  
  
## <a name="see-also"></a>Consulte também  
 [Relatório do perfil de execução](../profiling/execution-profile-report.md)   
 [Exibição de Threads](../profiling/threads-view-parallel-performance.md)