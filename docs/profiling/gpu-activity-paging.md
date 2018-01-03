---
title: "Atividade de GPU (paginação) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 01c61fb193ebc29c6eb76615e339327e71c24002
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="gpu-activity-paging"></a>Atividade de GPU (paginação)
Os segmentos de **Atividade de GPU (paginação)** na guia Threads representam o tempo durante o qual a GPU estava processando solicitações de paginação.  O tamanho de um segmento representa o tempo durante o qual a GPU estava processando um pacote de paginação de DMA (acesso direto à memória). Normalmente, pacotes de paginação são associados à transferência de memória entre a CPU e a GPU.  
  
 Quando você seleciona um segmento de paginação da GPU, o relatório na guia **Atual** exibe informações sobre o pacote de DMA que foi processado. Isso inclui a quantidade de tempo que ele esperou na fila de hardware associada ao mecanismo do DirectX, o processo que enviou o pacote de DMA e o tempo necessário para processar o pacote.  
  
## <a name="see-also"></a>Consulte também  
 [Exibição da utilização](../profiling/utilization-view.md)