---
title: "Relatório de operações de disco (exibição de threads) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.report.diskoperations
helpviewer_keywords: Concurrency Visualizer, File Operations Report (Threads View)
ms.assetid: e352f4f3-f654-45eb-96ed-417863487ddc
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a30a37f5003d407edb46ab3d4475b99f5bbe54ab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="disk-operations-report-threads-view"></a>Relatório de operações de disco (exibição de threads)
O relatório de operações de disco mostra operações de E/S de disco em canais de disco.  
  
 Para cada acesso ao disco que ocorre em nome do processo que está sendo atribuído na janela de tempo visível no momento, essas informações são relatadas:  
  
-   O nome e o PID do processo que executou o acesso ao disco  
  
-   A ID do thread que acessou o disco  
  
-   O nome do arquivo que foi acessado  
  
-   O número de leituras por arquivo  
  
-   O número de bytes lidos  
  
-   A latência de leitura, em milissegundos  
  
-   O número de gravações  
  
-   O número de bytes gravados  
  
-   A latência de gravação, em milissegundos  
  
## <a name="see-also"></a>Consulte também  
 [Exibição de Threads](../profiling/threads-view-parallel-performance.md)