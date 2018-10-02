---
title: Avaliação da expressão no modo de interrupção | Microsoft Docs
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
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a74119edfb390dab0a8ce0fddd96046ca80ad92d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47476147"
---
# <a name="expression-evaluation-in-break-mode"></a>Avaliação de expressão no modo de interrupção
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [avaliação de expressão no modo de interrupção](https://docs.microsoft.com/visualstudio/extensibility/debugger/expression-evaluation-in-break-mode).  
  
O exemplo a seguir descreve o processo que ocorre quando o depurador está no modo de interrupção e deverá conduzir a avaliação da expressão.  
  
## <a name="expression-evaluation-process"></a>Processo de avaliação de expressão  
 Estas são as etapas básicas envolvidas na avaliação de uma expressão:  
  
1.  O Gerenciador de sessão de depuração (SDM) chama [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obter uma interface de contexto de expressão, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2.  Em seguida, chama o SDM [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) com a cadeia de caracteres a ser analisada.  
  
3.  Se ParseText retornar S_OK, o motivo do erro é retornado.  
  
     -Caso contrário-  
  
     Se ParseText retornar S_OK, o SDM, em seguida, pode chamar o [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para obter um valor final da expressão analisada.  
  
    -   No caso de uso `IDebugExpression2::EvaluateSync`, a interface de retorno de chamada fornecido é usada para comunicar-se o processo contínuo de avaliação. O valor final é retornado em uma [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface.  
  
    -   No caso de uso `IDebugExpression2::EvaluateAsync`, a interface de retorno de chamada fornecido é usada para comunicar-se o processo contínuo de avaliação. Depois que a avaliação for concluída, EvaluateAsync envia um [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interface por meio do retorno de chamada. Com essa interface de eventos, o valor final pode ser obtido com [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>Consulte também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)

