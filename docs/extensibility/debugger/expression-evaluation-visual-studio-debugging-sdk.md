---
title: Avaliação de expressão (depuração do Visual Studio SDK) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 022a0ee21b7a58fdd69249b240490fc3c1df8361
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Avaliação de expressão (Visual Studio SDK de depuração)
Durante o modo de interrupção, o IDE deve ser capaz de avaliar expressões simples envolvendo diversas variáveis do programa. Para fazer isso, o mecanismo de depuração (DE) deve ser capaz de analisar e avaliar uma expressão que é inserida em uma das janelas do IDE.  
  
 As expressões são criadas usando o [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método e são representados por resultante [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface.  
  
 O **IDebugExpression2** interface é implementada pelas chamadas e DE seu **EvalAsync** método para retornar um [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface IDE, para exibir o resultados da avaliação de expressão no IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) retorna uma estrutura que pode ser usada para colocar o valor de uma expressão em uma janela de observação ou a janela locais.  
  
 A depuração pacote ou a sessão de depuração Gerenciador (SDM) chama [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) ou [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para obter um [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface que representa o resultado da avaliação. `IDebugProperty2` tem métodos que retornam o nome, tipo e valor da expressão. Essas informações são exibidas em várias janelas do depurador.  
  
## <a name="using-expression-evaluation"></a>Usando a avaliação de expressão  
 Para usar a avaliação da expressão, você deve implementar o [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método e todos os métodos do [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) de interface, conforme mostrado na tabela a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Avalia uma expressão de forma assíncrona.|  
|[Anular](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termina a avaliação da expressão assíncrona.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Avalia uma expressão de forma síncrona.|  
  
 Avaliação síncrona e assíncrona requerem a implementação do [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) método. Avaliação de expressão assíncrona requer a implementação de [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>Consulte também  
 [Controle de execução e avaliação de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)