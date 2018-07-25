---
title: Implementando um avaliador de expressão | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8bdf4f290c3312be234f491debe95f532c85802b
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232501"
---
# <a name="implement-an-expression-evaluator"></a>Implementar um avaliador de expressão
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão de CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Avaliar uma expressão é uma interação complexa entre o mecanismo de depuração (DE), o provedor de símbolo (SP), o objeto de associador e o avaliador de expressão (EE). Estes quatro componentes é conectado por interfaces que são implementados por um componente e consumidos por outro.  
  
 O EE usa uma expressão de na forma de uma cadeia de caracteres e analisa ou avalia a ele. O EE executa as seguintes interfaces são consumidas por um DE:  
  
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
  
 Executa o EE [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md). `IDebugProperty2` fornece o mecanismo para descrever o resultado de uma avaliação de expressão, como uma variável local, um primitivo ou um objeto para o Visual Studio, que, em seguida, exibe as informações apropriadas na **Locals**, **Watch** , ou **imediato** janela.  
  
 O SP é fornecido para o EE DE quando ele solicita informações. O SP será executado a interfaces que descrevem endereços e campos, como as interfaces a seguir e seus derivados:  
  
-   [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
 O EE consome todas essas interfaces.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Estratégia de implementação do avaliador de expressão](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 Define um processo de três etapas para a estratégia de implementação de (EE) do avaliador de expressão.  
  
## <a name="see-also"></a>Consulte também  
 [Escrever um avaliador de expressão de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)