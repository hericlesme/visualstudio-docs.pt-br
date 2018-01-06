---
title: "Avaliador de expressão | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 55aaa595c49d0c50cff5f874d1b322c3adbb9729
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="expression-evaluator"></a>Avaliador de expressão
Avaliadores de expressão (EE) examinam a sintaxe de um idioma para analisar e avaliar expressões e variáveis em tempo de execução, permitindo que eles sejam exibidos pelo usuário quando o IDE no modo de interrupção.  
  
## <a name="using-expression-evaluators"></a>Usando avaliadores de expressão  
 As expressões são criadas usando o [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método, da seguinte maneira:  
  
1.  O mecanismo de depuração (DE) implementa a [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface.  
  
2.  Obtém o pacote de depuração um `IDebugExpressionContext2` de objeto um [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interface e, em seguida, chama o `IDebugStackFrame2::ParseText` método para obter um [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto.  
  
3.  As chamadas de pacote de depuração a [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) método ou o [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) método para obter o valor da expressão. `IDebugExpression2::EvaluateAsync`é chamado da janela de comando/imediato. Todos os outros componentes de interface do usuário chamar `IDebugExpression2::EvaluateSync`.  
  
4.  O resultado da avaliação da expressão é um [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto, que contém o nome, o tipo e o valor do resultado da avaliação de expressão.  
  
 Durante a avaliação da expressão, o EE requer informações do componente do provedor de símbolo. O provedor de símbolo fornece as informações simbólicas usadas para identificar e compreender expressão analisada.  
  
 Quando a avaliação da expressão assíncrona for concluída, um evento assíncrono é enviado por DE por meio do Gerenciador de sessão de depuração (SDM) para notificar o IDE que a avaliação de expressão foi concluída. Quando a avaliação da expressão síncrona for concluída, o resultado da avaliação é retornado da chamada para o `IDebugExpression2::EvaluateSync` método.  
  
## <a name="implementation-notes"></a>Notas de implementação  
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mecanismos de depuração esperam para se comunicar com o avaliador de expressão usando as interfaces do Common Language Runtime (CLR). Como resultado, um avaliador de expressão que funciona com o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mecanismos de depuração devem oferecer suporte o CLR (uma lista completa de CLR de todas as interfaces de depuração pode ser encontrada em debugref.doc, que é parte do [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]).  
  
## <a name="see-also"></a>Consulte também  
 [Componentes do depurador](../../extensibility/debugger/debugger-components.md)