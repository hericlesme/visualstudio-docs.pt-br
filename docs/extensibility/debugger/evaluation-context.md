---
title: Contexto de avaliação | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 266fe85bedeea2c7e3dae7726d113d66a4b2b1e8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="evaluation-context"></a>Contexto de avaliação
> [!IMPORTANT]
>  No Visual Studio 2015, essa maneira de implementar avaliadores de expressão foi preterida. Para obter informações sobre como implementar avaliadores de expressão do CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quando o mecanismo de depuração (DE) chama o avaliador de expressão (EE), três argumentos passados para [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) determinar o contexto para localizar e avaliar símbolos, como mostrado na tabela a seguir.  
  
## <a name="arguments"></a>Arguments  
  
|Argumento|Descrição|  
|--------------|-----------------|  
|`pSymbolProvider`|Um [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) interface que especifica o manipulador de símbolo (SH) a ser usado para identificar o símbolo.|  
|`pAddress`|Um [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) interface que especifica o ponto atual de execução. Isso pode ser usado para localizar o método que contém o código que está sendo executado.|  
|`pBinder`|Um [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) interface que pode ser usado para localizar o valor e o tipo de um símbolo recebe seu nome.|  
  
 `IDebugParsedExpression::EvaluateSync` Retorna um [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface que representa o valor resultante e seu tipo.  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do avaliador de expressão de chave](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Exibir locais](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)