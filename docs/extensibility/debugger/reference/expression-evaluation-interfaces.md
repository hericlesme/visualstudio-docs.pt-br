---
title: "Interfaces de avaliação de expressão | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c6a9d1d63b4fb15a920f175013af8a05cb38beb8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="expression-evaluation-interfaces"></a>Interfaces de avaliação de expressão
> [!IMPORTANT]
>  No Visual Studio 2015, essa maneira de implementar avaliadores de expressão foi preterida. Para obter informações sobre como implementar avaliadores de expressão do CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 A seguir estão as Interfaces de avaliação de expressão para o [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] SDK de depuração.  
  
## <a name="discussion"></a>Discussão  
 Essas interfaces são usadas para avaliar expressões em uma pilha de chamadas durante o modo de interrupção. Eles são implementados apenas para avaliadores de expressão de tempo de execução do common language (EE).  
  
 Cada interface na tabela mostra o componente que possa implementá-la na lista a seguir:  
  
-   Depurar mecanismo (DE)  
  
-   Avaliador de expressão (EE)  
  
-   O Visual Studio (VS)  
  
|Interface|Implementado pelo|Descrição|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Representa um alias numérico para uma variável.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Representa um alias numérico para uma variável e permite que um avaliador de expressão (EE) para obter o domínio de aplicativo para o alias.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Representa um objeto de matriz.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Representa um objeto de matriz gerenciada e permite que um avaliador de expressão (EE) para determinar o índice de base (limite inferior) para a matriz.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Representa um associador que associa os símbolos para endereços reais na memória de depuração.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|Mesmo que o [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) interface mas fornece acesso aos tipos, aliases e os visualizadores personalizados.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Representa o avaliador de expressão.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Representa uma versão aprimorada de um avaliador de expressão (EE).|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Representa um avaliador de expressão (EE) com uma árvore de analisador aprimorados.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Representa uma função.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Representa uma função e aprimora o [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface.|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Permite que um avaliador de expressão (EE) exibir uma mensagem na janela de saída do depurador.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Representa um objeto de código gerenciado.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Interface base que representa qualquer símbolo associado a um endereço de memória.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|Mesmo que o [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface mas fornece acesso às informações adicionais.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Representa uma expressão analisada pronta para ser avaliada.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Representa um ponteiro.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Representa um ponteiro em uma árvore de análise e estende o **IDebugPointerObject** interface.|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Fornece a capacidade de modificar o valor do tipo por meio de um visualizador de tipo.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Fornece acesso aos visualizadores personalizados e visualizadores de tipo.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Fornece a capacidade de criar um [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) objeto.|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Representa uma coleção de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objetos.|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Escrevendo um avaliador de expressão de CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Visualizador de Tipo e Visualizador Personalizado](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)