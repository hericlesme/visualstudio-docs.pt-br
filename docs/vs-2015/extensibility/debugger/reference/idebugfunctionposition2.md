---
title: IDebugFunctionPosition2 | Microsoft Docs
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
- IDebugFunctionPosition2
helpviewer_keywords:
- IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 65726f1f2f05a459c07687e2a77f9db0dcb0b45a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464757"
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugFunctionPosition2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugfunctionposition2).  
  
Essa interface representa uma posição abstrata de uma função em um documento de origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugFunctionPosition2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DES) implementa essa interface para representar a posição de uma função dentro de um documento de origem.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é fornecida como parte de um [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) união (especificamente, um [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) estrutura) que por sua vez faz parte dos [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) estrutura, usada na criação de um ponto de interrupção pendente.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDebugFunctionPosition2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Obtém o nome da função que esta posição é relativo.|  
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|Obtém o deslocamento do início da função.|  
  
## <a name="remarks"></a>Comentários  
 A posição representada por esta interface é baseado em texto, especificamente, uma [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estrutura.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Principais Interfaces](../../../extensibility/debugger/reference/core-interfaces.md)   
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)

