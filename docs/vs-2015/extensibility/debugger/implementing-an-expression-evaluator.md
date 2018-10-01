---
title: Implementando um avaliador de expressão | Microsoft Docs
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
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d80688af9c574c522a1151c700d2ab117f4206d8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47460594"
---
# <a name="implementing-an-expression-evaluator"></a>Implementando um avaliador de expressão
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [implementando um avaliador de expressão](https://docs.microsoft.com/visualstudio/extensibility/debugger/implementing-an-expression-evaluator).  
  
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão de CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Avaliar uma expressão é uma interação complexa entre o mecanismo de depuração (DE), o provedor de símbolo (SP), o objeto de associador e o avaliador de expressão (EE) em si. Estes quatro componentes é conectado por interfaces que são implementados por um componente e consumidos por outro.  
  
 O EE usa uma expressão de na forma de uma cadeia de caracteres e analisa ou avalia a ele. O EE implementa as seguintes interfaces são consumidas por um DE:  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
 O EE chama o objeto de fichário, fornecido pelo DE, para obter o valor de símbolos e objetos. O EE consome as seguintes interfaces são implementadas por um DE:  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
-   [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
-   [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
-   [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
-   [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
-   [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
 Implementa o EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` fornece o mecanismo para descrever o resultado de uma avaliação de expressão, como uma variável local, um primitivo ou um objeto, para o Visual Studio, que, em seguida, exibe as informações apropriadas na **Locals**,  **Assista**, ou **imediato** janela.  
  
 O SP é fornecido para o EE DE quando ele solicita informações. O SP implementa as interfaces que descrevem endereços e campos, como as interfaces a seguir e seus derivados:  
  
-   [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
 O EE consome todas essas interfaces.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Estratégia de implementação do Avaliador de expressão](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Define um processo de três etapas para a estratégia de implementação de (EE) do avaliador de expressão.  
  
## <a name="see-also"></a>Consulte também  
 [Escrevendo um avaliador de expressão do CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

