---
title: Exemplo de implementação de locais | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 56ac92989abe929884ac029e3b9c9c7dafad5fd9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130473"
---
# <a name="sample-implementation-of-locals"></a>Exemplo de implementação de locais
> [!IMPORTANT]
>  No Visual Studio 2015, essa maneira de implementar avaliadores de expressão foi preterida. Para obter informações sobre como implementar avaliadores de expressão do CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Aqui está uma visão geral de como o Visual Studio obtém locais para um método do avaliador de expressão (EE):  
  
1.  O mecanismo de depuração (DE) o Visual Studio chama [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) para obter um [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto que representa todas as propriedades do quadro de pilha, incluindo os locais.  
  
2.  `IDebugStackFrame2::GetDebugProperty` chamadas [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) para obter um objeto que descreve o método no qual o ponto de interrupção ocorreu. O DE fornece um provedor de símbolo ([IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)), um endereço ([IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)) e um associador ([IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)).  
  
3.  `IDebugExpressionEvaluator::GetMethodProperty` chamadas [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) com fornecido `IDebugAddress` objeto para obter um [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) que representa o método que contém o endereço especificado.  
  
4.  O `IDebugContainerField` interface é consultada para o [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) interface. É essa interface que fornece acesso aos locais do método.  
  
5.  `IDebugExpressionEvaluator::GetMethodProperty` instancia uma classe (chamado `CFieldProperty` no exemplo) que implementa o `IDebugProperty2` interface para representar os locais do método. O `IDebugMethodField` objeto é colocado na `CFieldProperty` objeto juntamente com o `IDebugSymbolProvider`, `IDebugAddress` e `IDebugBinder` objetos.  
  
6.  Quando o `CFieldProperty` é inicializado, [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) é chamado no `IDebugMethodField` para obter um [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) estrutura que contém todas as informações de exibição sobre o próprio método .  
  
7.  `IDebugExpressionEvaluator::GetMethodProperty` Retorna o `CFieldProperty` de objeto como um `IDebugProperty2` objeto.  
  
8.  Chamadas do Visual Studio [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) no `IDebugProperty2` objeto com o filtro `guidFilterLocalsPlusArgs`. Isso retorna um [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) objeto que contém os locais do método. Essa enumeração é preenchida por chamadas para [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) e [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).  
  
9. Chamadas do Visual Studio [próximo](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) para obter um [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) estrutura para cada local. Essa estrutura contém um ponteiro para um `IDebugProperty2` interface para um local.  
  
10. Chamadas do Visual Studio [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) para cada local obter o nome, valor e tipo de local. Essas são as informações exibidas no **locais** janela.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Implementar GetMethodProperty](../../extensibility/debugger/implementing-getmethodproperty.md)  
 Descreve uma implementação de [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).  
  
 [Enumerar Locals](../../extensibility/debugger/enumerating-locals.md)  
 Descreve como o mecanismo de depuração (DE) faz uma chamada para enumerar argumentos ou variáveis locais.  
  
 [Obter as propriedades do Local](../../extensibility/debugger/getting-local-properties.md)  
 Descreve como o DE faz uma chamada para obter o nome, o tipo e o valor de um ou mais locais.  
  
 [Obter valores de Local](../../extensibility/debugger/getting-local-values.md)  
 Discute como obter o valor do local, que exige que os serviços de um objeto de fichário fornecido pelo contexto de avaliação.  
  
 [Avaliar Locals](../../extensibility/debugger/evaluating-locals.md)  
 Explica como os locais são avaliados.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Contexto da avaliação](../../extensibility/debugger/evaluation-context.md)  
 Fornece os argumentos que são passados quando a DE chama o avaliador de expressão (EE).  
  
 [Exemplo de MyCEE](http://msdn.microsoft.com/en-us/624a018b-9179-402f-9d48-3aec87b48f4f)  
 Demonstra uma abordagem de implementação para criar um avaliador de expressão para o idioma MyC.  
  
## <a name="see-also"></a>Consulte também  
 [Exibir Locals](../../extensibility/debugger/displaying-locals.md)