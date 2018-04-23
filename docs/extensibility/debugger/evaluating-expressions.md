---
title: Avaliação de expressões | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 47de275d63f5be1743408aa93c971dcff2959c25
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="evaluating-expressions"></a>Avaliando expressões
As expressões são criadas de cadeias de caracteres passadas do Autos, inspeção, QuickWatch ou windows imediatas. Quando uma expressão é avaliada, ele gera uma cadeia de caracteres imprimível que contém o nome e o tipo de variável ou argumento e seu valor. Essa cadeia de caracteres é exibida na janela do IDE correspondente.  
  
## <a name="implementation"></a>Implementação  
 Expressões são avaliadas quando um programa foi interrompido no ponto de interrupção. A expressão em si é representada por um [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface, que representa uma expressão analisada está pronta para a associação e avaliação dentro do contexto de avaliação da expressão especificada. O quadro de pilhas determina o contexto de avaliação de expressão, que fornece o mecanismo de depuração (DE) Implementando a [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface.  
  
 Recebe uma cadeia de caracteres de usuário e uma [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface, um mecanismo de depuração (DE) pode obter um [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface passando a cadeia de caracteres do usuário para o [ IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método. A interface IDebugExpression2 retornada contém a expressão analisada pronta para avaliação.  
  
 Com o `IDebugExpression2` interface, o DE pode obter o valor da expressão por meio da avaliação de expressão síncronas ou assíncronas, usando [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Esse valor, junto com o nome e o tipo da variável ou argumento, é enviado para o IDE para exibição. O valor, o nome e o tipo são representados por um [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface.  
  
 Para habilitar a avaliação da expressão, um DE deve implementar o [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) e [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaces. Avaliação síncrona e assíncrona requerem a implementação do [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [Quadros de pilhas](../../extensibility/debugger/stack-frames.md)   
 [Contexto de avaliação de expressão](../../extensibility/debugger/expression-evaluation-context.md)   
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)