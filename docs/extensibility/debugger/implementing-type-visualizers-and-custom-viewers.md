---
title: "Implementação de visualizadores de tipo e visualizadores personalizados | Microsoft Docs"
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
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 19718425df6f0c8a656db0e3d7ebf0f06937f780
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-type-visualizers-and-custom-viewers"></a>Visualizadores de tipo de implementação e visualizadores personalizados
> [!IMPORTANT]
>  No Visual Studio 2015, essa maneira de implementar avaliadores de expressão foi preterida. Para obter informações sobre como implementar avaliadores de expressão do CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Visualizadores de tipo e visualizadores personalizados permitem que um usuário exibir dados de um tipo específico de forma que seja mais significativa do que um despejo hexadecimal simple de números. Um avaliador de expressão (EE) pode associar visualizadores personalizados com tipos específicos de dados ou variáveis. Visualizadores personalizados são implementados fazendo o EE. O EE também pode dar suporte a visualizadores de tipo externo, o que podem vir de outro fornecedor de terceiros ou até mesmo o usuário final.  
  
## <a name="discussion"></a>Discussão  
  
### <a name="type-visualizers"></a>Visualizadores de tipo  
 O Visual Studio solicita uma lista de visualizadores de tipo e visualizadores personalizados para cada objeto a ser exibido em uma janela inspeção. Um avaliador de expressão (EE) fornece essa lista para todos os tipos para os quais deseja dar suporte a visualizadores de tipo e visualizadores personalizados. Chamadas para [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) e [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) iniciar todo o processo de acessar os visualizadores de tipo e visualizadores personalizados (consulte [Visualizing e exibindo dados](../../extensibility/debugger/visualizing-and-viewing-data.md)para obter detalhes sobre a sequência de chamada).  
  
### <a name="custom-viewers"></a>Visualizadores personalizados  
 Visualizadores personalizados são implementados no EE para um tipo de dados específico e são representados pelo [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interface. Um visualizador personalizado não é tão flexível, como um visualizador de tipo, desde que ele está disponível somente quando o EE que implementa esse visualizador personalizado específico está em execução. Implementar um visualizador personalizado é mais simples de implementar o suporte a visualizadores de tipo. No entanto, dando suporte a visualizadores de tipo fornece máxima flexibilidade para o usuário final para a visualização de dados de seu. O restante desta discussão aborda apenas os visualizadores de tipo.  
  
## <a name="interfaces"></a>Interfaces  
 O EE implementa as interfaces a seguir para dar suporte a visualizadores de tipo a ser consumido pelo Visual Studio:  
  
-   [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
-   [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
-   [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
-   [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
-   [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
 O EE consome as seguintes interfaces para dar suporte a visualizadores de tipo:  
  
-   [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
-   [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
-   [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## <a name="see-also"></a>Consulte também  
 [Escrevendo um avaliador de expressão de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualizando e exibindo dados](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)