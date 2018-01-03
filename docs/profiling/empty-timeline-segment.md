---
title: Segmento da linha do tempo vazio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.empty
helpviewer_keywords: Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 026c6cd05ae926228cab5ab2cb52d389cd021d2a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="empty-timeline-segment"></a>Segmento da linha de tempo vazio
Na Visualização Simultânea, o motivo pelo qual uma seção da linha do tempo está vazia (tem uma tela de fundo branca) depende do tipo de canal.  
  
-   Para um canal de thread de CPU, isso significa que o thread não existia durante esta parte da linha do tempo. Se estiver interessado no thread, você poderá encontrar sua seção de execução usando o controle de aplicação de zoom ou rolando horizontalmente.  
  
-   Para um canal de E/S, significa que nenhum acesso ao disco ocorreu em nome do processo de destino no momento.  
  
-   Para um canal do DirectX, significa que nenhum trabalho de GPU foi executado em nome do processo de destino durante esta parte da linha do tempo.  
  
-   Para um canal de marcador, significa que nenhum marcador foi gerado.  
  
## <a name="see-also"></a>Consulte também  
 [Exibição Threads](../profiling/threads-view-parallel-performance.md)   
 [Controle de zoom (exibição de Threads)](../profiling/zoom-control-threads-view.md)