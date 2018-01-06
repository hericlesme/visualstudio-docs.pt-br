---
title: "Contexto de avaliação | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9a490ef7c4ea42fe85c291ee913d7ad5e1cda1bb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
  
 `IDebugParsedExpression::EvaluateSync`Retorna um [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface que representa o valor resultante e seu tipo.  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces do avaliador de expressão de chave](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Exibir locais](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)