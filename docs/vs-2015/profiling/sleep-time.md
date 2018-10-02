---
title: Tempo de Suspensão | Microsoft Docs
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
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd4d12097a8bf952cc0af0fa99025b9747ee7b3f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474419"
---
# <a name="sleep-time"></a>Tempo de suspensão
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [tempo de suspensão](https://docs.microsoft.com/visualstudio/profiling/sleep-time).  
  
Esses segmentos na linha do tempo estão associados os tempos de bloqueio categorizados como Suspensão. A categoria de suspensão indica que um thread voluntariamente cedeu seu núcleo lógico e não está trabalhando. Durante esse tempo, um thread foi bloqueado em uma API que a Visualização Simultânea está contando como suspensão. APIs como `Sleep()` e `SwitchToThread()` pertencem a esse grupo.  
  
## <a name="see-also"></a>Consulte também  
 [Exibição de Threads](../profiling/threads-view-parallel-performance.md)



