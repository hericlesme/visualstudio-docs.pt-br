---
title: Atividade de GPU (paginação) | Microsoft Docs
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
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c11bd0fd8f348ff90e95660e5df03a4aa591d96
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462029"
---
# <a name="gpu-activity-paging"></a>Atividade de GPU (paginação)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [atividade de GPU (paginação)](https://docs.microsoft.com/visualstudio/profiling/gpu-activity-paging).  
  
Os segmentos de **Atividade de GPU (paginação)** na guia Threads representam o tempo durante o qual a GPU estava processando solicitações de paginação.  O tamanho de um segmento representa o tempo durante o qual a GPU estava processando um pacote de paginação de DMA (acesso direto à memória). Normalmente, pacotes de paginação são associados à transferência de memória entre a CPU e a GPU.  
  
 Quando você seleciona um segmento de paginação da GPU, o relatório na guia **Atual** exibe informações sobre o pacote de DMA que foi processado. Isso inclui a quantidade de tempo que ele esperou na fila de hardware associada ao mecanismo do DirectX, o processo que enviou o pacote de DMA e o tempo necessário para processar o pacote.  
  
## <a name="see-also"></a>Consulte também  
 [Exibição da utilização](../profiling/utilization-view.md)



