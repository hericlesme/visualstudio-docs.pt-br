---
title: "A avaliação da expressão no modo de interrupção | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: cd28633fcb4b8186dae154428e489d51041aa8b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="expression-evaluation-in-break-mode"></a>Avaliação da expressão no modo de interrupção
O exemplo a seguir descreve o processo que ocorre quando o depurador está no modo de interrupção e deve realizar a avaliação da expressão.  
  
## <a name="expression-evaluation-process"></a>Processo de avaliação de expressão  
 Estas são as etapas básicas envolvidas na avaliação de uma expressão:  
  
1.  O Gerenciador de sessão de depuração (SDM) chama [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obter uma interface de contexto de expressão, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2.  Em seguida, chama o SDM [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) com a cadeia de caracteres a ser analisada.  
  
3.  Se ParseText não retorna S_OK, o motivo do erro será retornado.  
  
     -Caso contrário  
  
     Se ParseText retornar S_OK, o SDM pode chamar o [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para obter um valor final da expressão analisada.  
  
    -   No caso de uso `IDebugExpression2::EvaluateSync`, a interface de retorno de chamada fornecida é usada para comunicar-se o processo contínuo de avaliação. O valor final é retornado em uma [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface.  
  
    -   No caso de uso `IDebugExpression2::EvaluateAsync`, a interface de retorno de chamada fornecida é usada para comunicar-se o processo contínuo de avaliação. Uma vez concluída a avaliação, EvaluateAsync envia um [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interface por meio do retorno de chamada. Com esta interface de evento, o valor final pode ser obtido com [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>Consulte também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)