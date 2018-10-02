---
title: Acompanhamento de arquivos | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 40598ba8fbe693d44ee49228a36be75a9e851eea
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462830"
---
# <a name="file-tracking"></a>Acompanhamento de arquivos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [arquivo de rastreamento](https://docs.microsoft.com/visualstudio/msbuild/file-tracking).  
  
  
O acompanhamento de arquivo registra chamadas no sistema de arquivos do Windows para um processo e seus processos filho. Ao chamar as funções listadas abaixo, os programas controlam quando ativar e desativar esse registro e especificar o arquivo de log a ser usado.  
  
## <a name="in-this-section"></a>Nesta seção  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 Para o acompanhamento no contexto atual.  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 Retomar acompanhamento após uma chamada para [SuspendTracking](../msbuild/suspendtracking.md).  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 Definir o número de threads a serem usados para acompanhamento.  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 Iniciar um novo contexto de acompanhamento.  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 Iniciar um novo contexto de acompanhamento com uma raiz especificada.  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 Finalizar acompanhamento e recursos da versão usados.  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 Suspender temporariamente o acompanhamento.  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 Gravar os logs de acompanhamento para todos os contextos.  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 Gravar os logs de acompanhamento para o contexto atual.



