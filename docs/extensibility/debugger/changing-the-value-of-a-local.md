---
title: Alterar o valor de um Local | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 422d1702f319db6da21892bcaa1bd50adad7909d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109579"
---
# <a name="changing-the-value-of-a-local"></a>Alterar o valor de um Local
> [!IMPORTANT]
>  No Visual Studio 2015, essa maneira de implementar avaliadores de expressão foi preterida. Para obter informações sobre como implementar avaliadores de expressão do CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quando um novo valor é digitado no campo de valor de **locais** janela, o pacote de depuração passa a cadeia de caracteres, como foi digitado para o avaliador de expressão (EE). O EE avalia essa cadeia de caracteres que pode conter um valor simples ou uma expressão e armazena o valor resultante no local associado.  
  
 Isso é uma visão geral do processo de alteração do valor de um local:  
  
1.  Depois que o usuário inserir o novo valor, o Visual Studio chama [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) no [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto associado ao local.  
  
2.  `IDebugProperty2::SetValueAsString` executa as seguintes tarefas:  
  
    1.  Avalia a cadeia de caracteres para produzir um valor.  
  
    2.  Associa o associado [IDebugField](../../extensibility/debugger/reference/idebugfield.md) para obter um [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objeto.  
  
    3.  Converte o valor em uma série de bytes.  
  
    4.  Chamadas [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) colocar bytes do valor na memória para o programa que está sendo depurado pode acessá-los.  
  
3.  O Visual Studio atualiza o **locais** exibir (consulte [exibindo locais](../../extensibility/debugger/displaying-locals.md) para obter detalhes).  
  
 Esse procedimento também é usado para alterar o valor de uma variável no **inspecionar** janela exceto se ele é o `IDebugProperty2` objeto associado com o valor do local que é usado em vez do `IDebugProperty2` objeto associado ao local em si.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Exemplo de implementação da alteração de valores](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Usa o exemplo MyCEE para percorrer o processo de alteração de valores.  
  
## <a name="see-also"></a>Consulte também  
 [Escrevendo um avaliador de expressão de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Exibir Locals](../../extensibility/debugger/displaying-locals.md)