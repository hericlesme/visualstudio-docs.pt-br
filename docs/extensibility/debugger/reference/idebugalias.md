---
title: IDebugAlias | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAlias
helpviewer_keywords: IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 128dc9001faba06b1c95c5ebc364f319891ce409
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugalias"></a>IDebugAlias
> [!IMPORTANT]
>  No Visual Studio 2015, essa maneira de implementar avaliadores de expressão foi preterida. Para obter informações sobre como implementar avaliadores de expressão do CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Representa um alias numérico para uma variável. Um alias é simplesmente um nome diferente para uma variável.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugAlias : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O avaliador de expressão (EE) implementa essa interface para oferecer suporte a aliases numéricos para variáveis.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md) cria um alias para um objeto específico. Para procurar os aliases, use [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) ou [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Os métodos a seguir são definidos no `IDebugAlias` interface.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Obtém o objeto ao qual este alias se refere.|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Obtém o nome do alias.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Recupera um `ICorDebugValue` gerenciado de interface que fornece acesso a informações de código sobre esse objeto (somente código gerenciado).|  
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Marca este alias como não sendo usados.|  
  
## <a name="remarks"></a>Comentários  
 Um alias é um número decimal em formato de cadeia de caracteres, seguido pelo caractere #, por exemplo, # 1001.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)   
 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)