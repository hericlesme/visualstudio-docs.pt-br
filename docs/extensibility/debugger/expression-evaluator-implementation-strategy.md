---
title: Estratégia de implementação do avaliador de expressão | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e67b2496c2e30428cd4cc830526e53cf0cc61fdd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31102428"
---
# <a name="expression-evaluator-implementation-strategy"></a>Estratégia de implementação do avaliador de expressão
> [!IMPORTANT]
>  No Visual Studio 2015, essa maneira de implementar avaliadores de expressão foi preterida. Para obter informações sobre como implementar avaliadores de expressão do CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Uma abordagem para criar rapidamente um avaliador de expressão (EE) é primeiro implementar o código mínimo necessário para exibir as variáveis locais no **locais** janela. É útil ter em mente que cada linha de **locais** janela exibe o nome, tipo e valor de uma variável local e que todos os três são representados por um [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto. O nome, tipo e valor de uma variável local podem ser obtidos um `IDebugProperty2` objeto chamando seu [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) método. Para obter mais informações sobre como exibir as variáveis locais no **locais** janela, consulte [exibindo locais](../../extensibility/debugger/displaying-locals.md).  
  
## <a name="discussion"></a>Discussão  
 A sequência de implementação possíveis inicia com a implementação [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md). O [analisar](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) e [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) métodos precisam ser implementados para exibir locais. Chamando `IDebugExpressionEvaluator::GetMethodProperty` retorna um `IDebugProperty2` objeto que representa um método: ou seja, um [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) objeto. Métodos não são exibidos no **locais** janela.  
  
 O [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) método deve ser implementado em seguida. O mecanismo de depuração (DE) chama esse método para obter uma lista de argumentos e variáveis locais, passando `IDebugProperty2::EnumChildren` um `guidFilter` argumento de `guidFilterLocalsPlusArgs`. `IDebugProperty2::EnumChildren` chamadas [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) e [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), combinando os resultados em uma única enumeração. Consulte [exibindo locais](../../extensibility/debugger/displaying-locals.md) para obter mais detalhes.  
  
## <a name="see-also"></a>Consulte também  
 [Implementando um avaliador de expressão](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Exibir Locals](../../extensibility/debugger/displaying-locals.md)