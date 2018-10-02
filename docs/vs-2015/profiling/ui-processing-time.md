---
title: Tempo de processamento de interface do usuário | Microsoft Docs
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
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e35f5f37b0eced2822cb4b019732210bec94495
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47473475"
---
# <a name="ui-processing-time"></a>Tempo de processamento de interface do usuário
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [tempo de processamento de interface do usuário](https://docs.microsoft.com/visualstudio/profiling/ui-processing-time).  
  
Esses segmentos na linha do tempo estão associados aos tempos de bloqueio categorizados como Processamento de Interface do Usuário. Isso significa que um thread está bombeando mensagens do Windows ou realizando outro trabalho de interface do usuário. Durante esse tempo, um thread foi bloqueado em uma API que a Visualização Simultânea está contando como Processamento de Interface do Usuário. APIs como `GetMessage()` e `MsgWaitForMultipleObjects()` pertencem a esse grupo.  
  
 Se nenhuma API de bloqueio predefinida for identificada, examine as pilhas de chamadas e relatórios de perfil para determinar as causas subjacentes do atraso.  
  
 A categoria de Processamento de Interface do Usuário é importante para compreender a capacidade de resposta dos aplicativos de GUI e é desejável em aplicativos que dependem da capacidade de resposta da interface do usuário. Por exemplo, se o thread de interface do usuário em um aplicativo alcançar 100% de tempo no Processamento de Interface do Usuário, provavelmente, ele terá uma grande capacidade de resposta. No entanto, se o thread de interface do usuário gastar um tempo considerável em outras categorias, procure as causas raiz e considere opções para reduzir categorias sem interface do usuário nesse thread.  
  
## <a name="see-also"></a>Consulte também  
 [Exibição de Threads](../profiling/threads-view-parallel-performance.md)



