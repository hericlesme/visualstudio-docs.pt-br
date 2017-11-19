---
title: IDebugManagedObject | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugManagedObject
helpviewer_keywords: IDebugManagedObject interface
ms.assetid: 3ae09d34-112c-4285-80ee-9f7f8dc414d7
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d876fd9b536a0d16ae0aef4daed7f4c92c62f250
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmanagedobject"></a>IDebugManagedObject
> [!IMPORTANT]
>  No Visual Studio 2015, essa maneira de implementar avaliadores de expressão foi preterida. Para obter informações sobre como implementar avaliadores de expressão do CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Essa interface permite que o avaliador de expressão (EE) para chamar métodos ou propriedades em instâncias de classe de valor (por exemplo, `System.Decimal`) e para definir seu valor sem chamar [avaliar](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) sobre o programa que está sendo depurado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugManagedObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um avaliador de expressão implementa essa interface para representar um objeto de código gerenciado, como uma variável.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Para obter essa interface, chame [GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md) em uma [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa uma instância de uma classe de valor.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Além dos métodos herdados de [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md), o `IDebugManagedObject` interface expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-getmanagedobject.md)|Retorna uma interface que representa o objeto de código gerenciado e de que qualquer código gerenciado apropriado interface pode ser obtida.|  
|[SetFromManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject.md)|Define o valor do objeto para o valor de um objeto de código gerenciado especificado.|  
  
## <a name="remarks"></a>Comentários  
 Um avaliador de expressão usa essa interface para armazenar um objeto de código gerenciado em uma árvore de análise.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Avaliar](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md)