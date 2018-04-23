---
title: Avaliar uma expressão de janela Inspeção | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: beb632b484659c3bc901142b35ab52d25b8067fe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="evaluating-a-watch-window-expression"></a>Avaliar uma expressão de janela Inspeção
> [!IMPORTANT]
>  No Visual Studio 2015, essa maneira de implementar avaliadores de expressão foi preterida. Para obter informações sobre como implementar avaliadores de expressão do CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quando a execução pausa, o Visual Studio chama o mecanismo de depuração (DE) para determinar o valor atual de cada expressão em sua lista de observação. O DE avalia cada expressão usando um avaliador de expressão (EE) e seu valor no Visual Studio exibe o **inspecionar** janela.  
  
 Aqui está uma visão geral de como uma expressão de lista de observação é avaliada:  
  
1.  O Visual Studio chama o DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obter um contexto de expressão que pode ser usado para avaliar expressões.  
  
2.  Para cada expressão na lista de monitoramento, o Visual Studio chama [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para converter o texto da expressão em uma expressão analisada.  
  
3.  `IDebugExpressionContext2::ParseText` chamadas [analisar](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para fazer o trabalho real de analisar o texto e produzir um [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objeto.  
  
4.  `IDebugExpressionContext2::ParseText` cria um [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto e coloca o `IDebugParsedExpression` objeto nele. Esse,`DebugExpression2` objeto, em seguida, é retornado para o Visual Studio.  
  
5.  Chamadas do Visual Studio [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para avaliar a expressão analisada.  
  
6.  `IDebugExpression2::EvaluateSync` passará a chamada para [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) para fazer a avaliação real e produzir um [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto que é retornado para o Visual Studio.  
  
7.  Chamadas do Visual Studio [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) para obter o valor da expressão que é exibido na lista de monitoramento.  
  
## <a name="parse-then-evaluate"></a>Analisar e avaliar  
 Como analisar uma expressão complexa pode demorar muito mais avaliá-lo, o processo de avaliação de uma expressão é dividido em duas etapas: 1) analisar a expressão e 2) Avaliar expressão analisada. Dessa forma, a avaliação pode ocorrer várias vezes, mas a expressão precisa ser analisada apenas uma vez. A expressão analisada intermediário é retornado de EE em um [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) objeto que é encapsulado por sua vez e retornado de como um [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto. O `IDebugExpression` objeto adia a avaliação de todos os `IDebugParsedExpression` objeto.  
  
> [!NOTE]
>  Não é necessário para um EE aderir a este processo de duas etapas, mesmo que o Visual Studio faz isso; o EE pode analisar e avaliar na mesma etapa quando [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) é chamado (Isso é como o exemplo MyCEE funciona, por exemplo). Se o seu idioma pode formar expressões complexas, convém separar a etapa de análise da etapa de avaliação. Isso pode aumentar o desempenho no depurador do Visual Studio quando muitas expressões de inspeção estão sendo mostradas.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Exemplo de implementação da Avaliação de expressão](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 Usa o exemplo MyCEE para percorrer o processo de avaliação de expressão.  
  
 [Avaliar uma expressão de Inspeção](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 Explica o que acontece após uma análise da expressão com êxito.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Contexto da avaliação](../../extensibility/debugger/evaluation-context.md)  
 Fornece os argumentos que são passados quando o mecanismo de depuração (DE) chama o avaliador de expressão (EE).  
  
## <a name="see-also"></a>Consulte também  
 [Escrevendo um avaliador de expressão de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)