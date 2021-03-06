---
title: Exibição de Módulos | Microsoft Docs
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
- vs.performance.view.modules
helpviewer_keywords:
- Modules view
- profiling tools reports, Modules view
- profiling tools, Modules view
ms.assetid: 4314a404-2120-425b-be42-180cd4bac840
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: baf208e30a96efa73e0524fc10a761ac01c316e9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47462064"
---
# <a name="modules-view"></a>Exibição de módulos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [exibição de módulos](https://docs.microsoft.com/visualstudio/profiling/modules-view).  
  
A exibição de Módulos lista os módulos dos dados de criação de perfil. Cada módulo é o nó raiz de uma árvore hierárquica. As funções que tiveram o perfil criado do módulo são listadas abaixo do nó do módulo. Se os dados de criação de perfil foram coletados usando o método de amostragem, as informações de linha são listadas sob o nó de função e os dados de ponteiro de instrução são listados sob o nó de linha.  
  
 Expandir ou recolher o nome do módulo para exibir ou fechar a exibição de dados de desempenho do módulo.  
  
 Para adicionar ou remover colunas, clique com o botão direito do mouse na janela do relatório e, em seguida, selecione **Adicionar/Remover Colunas**. Você pode classificar os dados em um nome de coluna. Para obter mais informações, consulte [Como personalizar colunas de exibição de relatório](../profiling/how-to-customize-report-view-columns.md).  
  
 As colunas que estão disponíveis na exibição de Módulos dependem do método de criação de perfil (amostragem ou instrumentação) usado para coletar os dados e se os dados de memória .NET foram coletados na execução da criação de perfil.  
  
## <a name="see-also"></a>Consulte também  
 [Exibição Módulos](../profiling/modules-view-sampling-data.md)   
 [Exibição Módulos](../profiling/modules-view-instrumentation-data.md)   
 [Exibição Módulos – Instrumentação](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Exibição Módulos – amostragem](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Exibição Módulos](../profiling/modules-view-contention-data.md)



