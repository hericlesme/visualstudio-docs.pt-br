---
title: Pilha de chamadas gráfico | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.callstack
ms.assetid: 8a30168d-8b39-4de1-b094-c7356ba101a3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 879189fe71a4bf9dc0b7c56afe81d85d4316b6a4
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474044"
---
# <a name="graphics-event-call-stack"></a>Pilha de chamadas de gráfico
A pilha de chamadas do evento gráficos no analisador de gráficos do Visual Studio ajuda você a mapear o relacionamento entre eventos de gráficos problemático e código-fonte do seu aplicativo.  
  
 Esta é a janela pilha de chamadas do evento:  
  
 ![A pilha de chamada anterior um evento DrawIndexed. ] (media/gfx_diag_demo_graphics_event_call_stack_orientation.png "gfx_diag_demo_graphics_event_call_stack_orientation")  
  
## <a name="understanding-the-graphics-event-call-stack"></a>Noções básicas sobre a pilha de chamadas do evento de gráficos  
 Você pode usar a pilha de chamadas do evento para entender o fluxo de execução que levou a um determinado evento Direct3D. Ele é semelhante a janela de pilha de chamada do Visual Studio, exceto que, em vez de exibir a pilha de chamadas atual do thread atual em um aplicativo em execução, ele exibe a pilha de chamadas que existia quando ocorreu o evento Direct3D selecionado. Da pilha de chamadas de evento, você pode ir para o site de chamada do evento selecionado Direct3D para inspecionar o código ao redor.  
  
 Ao usar a pilha de chamadas do evento para identificar o caminho do código de origem de um evento de problema, você pode usar seu conhecimento da Base de código para deduzir possíveis fontes do problema, ou você pode adicionar pontos de interrupção no código-fonte do seu aplicativo para que você possa usar tradicional técnicas para examinar como o estado dos parâmetros de aplicativo ou eventos estão causando o evento misbehave de depuração. Esse exame pode ajudá-lo a encontrar problemas no código-fonte que são manifestados somente como problemas de renderização.  
  
### <a name="graphics-event-call-stack-information"></a>Informações sobre a pilha de chamadas de gráfico  
 A pilha de chamadas do evento não dá suporte a eventos de quadros pré ou eventos definidos pelo usuário. A pilha de chamadas de eventos de gráficos é exibida em um formato de tabela.  
  
|Coluna|Descrição|  
|------------|-----------------|  
|**Nome**|Um símbolo que identifica a função que contém o site de chamada. O símbolo de depuração da função é exibido quando ela está disponível. Caso contrário, o deslocamento de função é exibido.|  
|**Arquivo**|O nome do arquivo do código-fonte ou arquivo de biblioteca que contém o site de chamada.|  
|**Local**|O número de linha do site de chamada.|  
  
### <a name="links-to-graphics-objects"></a>Links a objetos de gráficos  
 Para entender o evento de gráfico selecionado, talvez seja necessário obter informações sobre os objetos de Direct3D que estão associados a ele. O **pilha de chamadas do evento de gráficos** janela fornece links para essas informações.  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: objetos ausentes devido ao sombreamento de vértice](walkthrough-missing-objects-due-to-vertex-shading.md)