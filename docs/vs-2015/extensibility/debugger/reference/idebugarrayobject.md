---
title: IDebugArrayObject | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugArrayObject
helpviewer_keywords:
- IDebugArrayObject method
ms.assetid: a1c8e77e-dee1-4748-a516-6ab032a8f54f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 02d8c9758dc12a5f19f489d1221446bd4b855c96
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475119"
---
# <a name="idebugarrayobject"></a>IDebugArrayObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugArrayObject](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugarrayobject).  
  
> [!IMPORTANT]
>  No Visual Studio 2015, essa forma de implementar os avaliadores de expressão foi preterida. Para obter informações sobre como implementar os avaliadores de expressão de CLR, consulte [avaliadores de expressão de CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Essa interface representa um objeto de matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugArrayObject : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O avaliador de expressão implementa essa interface para representar uma matriz.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface pode obter essa interface usando [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) se o objeto representa uma matriz.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 Além dos métodos na `IDebugObject` interface, os seguintes métodos são implementados no `IDebugArrayObject` interface.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md)|Obtém a contagem de elementos na matriz.|  
|[GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)|Obtém um elemento da matriz.|  
|[GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)|Obtém todos os elementos da matriz.|  
|[GetRank](../../../extensibility/debugger/reference/idebugarrayobject-getrank.md)|Obtém a classificação da matriz.|  
|[GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)|Obtém as dimensões da matriz.|  
  
## <a name="remarks"></a>Comentários  
 Um avaliador de expressão usa essa interface para representar matrizes em uma árvore de análise.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

