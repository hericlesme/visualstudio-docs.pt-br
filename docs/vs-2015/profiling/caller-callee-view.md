---
title: Exibição de chamador-computador chamado | Microsoft Docs
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
- vs.performance.view.callercallee
helpviewer_keywords:
- profiling tools, reports, Caller/Callee view
- profiling tools, Caller/Callee view
- performance reports, Caller/Callee view
- Caller/Callee view
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
caps.latest.revision: 37
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a28f0184d126781c43540d447cd75cd905e15d40
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462959"
---
# <a name="callercallee-view"></a>Exibição Chamador/Receptor da Chamada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [modo de exibição de chamador / computador chamado](https://docs.microsoft.com/visualstudio/profiling/caller-callee-view).  
  
A exibição de Chamador/Computador Chamado exibe informações de perfil para uma função selecionada e suas funções pai e filho. A exibição de Chamador/Computador Chamado contém três grades:  
  
 **Função atual** é exibida na grade intermediária e mostra informações de criação de perfil para a função selecionada. Os valores incluem todas as chamadas para a função que foram coletadas na execução de criação de perfil.  
  
 **Funções que chamaram a função atual** são exibidas na grade superior e mostram o número dos valores da função selecionada (atual) gerados por chamadas da função de chamador (pai).  
  
 **Funções que foram chamadas pela função atual** são exibidas na grade inferior e mostram informações de criação de perfil para as funções do computador chamado (filho) da função selecionada quando a função filho foi chamada pela função atual.  
  
 As colunas que estão disponíveis na exibição de Chamador/Computador Chamado dependem do método de criação de perfil (amostragem ou instrumentação) usado para coletar os dados e de se os dados de memória do .NET foram coletados na execução da criação de perfil.  
  
 Você pode selecionar uma função diferente para ser a Função Atual na parte do meio da exibição de Relatório clicando duas vezes em qualquer uma das funções listadas nas outras duas partes da exibição. A exibição de Relatório é atualizada automaticamente para refletir as alterações.  
  
 Você pode classificar os dados clicando em nomes de coluna. Colunas adicionais podem ser incluídas na exibição de Chamador/Computador Chamado. Para obter mais informações, consulte [Como personalizar colunas de exibição de relatório](../profiling/how-to-customize-report-view-columns.md).  
  
## <a name="see-also"></a>Consulte também  
 [Exibição de chamador/computador chamado – dados de amostragem](../profiling/caller-callee-view-sampling-data.md)   
 [Exibição de chamador/computador chamado – dados de instrumentação](../profiling/caller-callee-view-instrumentation-data.md)   
 [Exibição Chamador/Receptor da Chamada – dados de instrumentação da memória do .NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Exibição Chamador/Receptor da Chamada – dados de amostragem da memória do .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Exibição do chamador/computador chamado – dados de contenção](../profiling/caller-callee-view-contention-data.md)



