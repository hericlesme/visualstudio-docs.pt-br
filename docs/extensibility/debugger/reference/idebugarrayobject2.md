---
title: IDebugArrayObject2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 13e522497a0046ebfc99c60c7c3d771acfd4fbca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
>  No Visual Studio 2015, essa maneira de implementar avaliadores de expressão foi preterida. Para obter informações sobre como implementar avaliadores de expressão do CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra do avaliador de expressão gerenciado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Representa um objeto de matriz gerenciada e permite que um avaliador de expressão (EE) para determinar o índice de base (limite inferior) para a matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugArrayObject2 : IDebugArrayObject  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Isso é implementado pelo mecanismo de depuração gerenciados (DE).  
  
## <a name="methods"></a>Métodos  
 Além dos métodos de [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) interface, essa interface implementa os métodos a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Recupera o índice de base (limites inferiores) para cada índice dado o número de dimensões da matriz.|  
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Determina se a matriz tem índices base (limites inferiores) definidos.|  
  
## <a name="remarks"></a>Comentários  
 Um avaliador de expressão usa essa interface para representar matrizes gerenciadas em uma árvore de análise.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll