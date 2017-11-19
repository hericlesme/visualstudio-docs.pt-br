---
title: Tipo de visualizador e o visualizador personalizado | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 80798887beee6116b3a93b5d8ec86b14269b5475
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="type-visualizer-and-custom-viewer"></a>Visualizador de tipo e o visualizador personalizado
Um visualizador de tipo é um componente que exibe uma parte dos dados em um formato muito específico. Esse formato é inteiramente o implementador do visualizador, o usuário final ou um fornecedor de terceiros de visualizadores.  
  
 Um visualizador personalizado é a parte de um avaliador de expressão personalizado que exibe uma parte dos dados em um formato muito específico. Esse formato é inteiramente o implementador de visualizador personalizado, o que significa que o formato é até o implementador de avaliador de expressão (EE).  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Suporte a visualizadores de tipo em um avaliador de expressão  
 Um EE pode dar suporte a visualizadores de tipo com suporte a um conjunto de interfaces acessíveis aos visualizadores: interfaces como [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) e [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). No entanto, observe que o EE não é responsável por implementar o Visualizador de tipo em si: o EE simplesmente permite que visualizadores externos acessem as informações de tipo. Tais visualizadores podem ser enviados junto com o EE e instalados no local adequado no Visual Studio, fornecido por outro fornecedor de terceiros ou até mesmo pelo usuário final.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Suporte a visualizadores personalizados em um avaliador de expressão  
 Um EE também pode dar suporte a visualizadores personalizados na qual o EE próprio fornece o código para exibir o tipo de dados. Um visualizador personalizado implementa o [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interface, que manipula todas as tarefas de mostrar os dados em qualquer formato desejado; o visualizador tem controle total sobre a exibição e até mesmo pode permitir que os dados sejam modificados. Qualquer visualizadores personalizados fornecidos pelo EE vêm com o EE quando o produto é enviado.  
  
## <a name="see-also"></a>Consulte também  
 [Componentes do depurador](../../extensibility/debugger/debugger-components.md)   
 [Avaliador de expressão](../../extensibility/debugger/expression-evaluator.md)   
 [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)