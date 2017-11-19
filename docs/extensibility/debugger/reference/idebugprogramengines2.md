---
title: IDebugProgramEngines2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgramEngines2
helpviewer_keywords: IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 99ff94445caf60edde57f4365abbb5241d61127d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Essa interface é usada por nós de programa para especificar todos os possíveis mecanismos de depuração (DE) que podem depurar este programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugProgramEngines2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um fornecedor de porta personalizada ou um DE implementa essa interface no mesmo objeto que implementa [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) para dar suporte ao estabelecimento DE específico a ser usado para um determinado programa.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamar [QueryInterface](/cpp/atl/queryinterface) em um `IDebugProgramNode2` interface para obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugProgramEngines2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Indica o DEs possíveis que podem depurar este programa.|  
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Seleciona o DE ser usado para depurar este programa.|  
  
## <a name="remarks"></a>Comentários  
 Depois que a DE é escolhida pelo usuário, essa opção está registrada com o nó de programa chamando [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md). O mecanismo selecionado torna-se o mecanismo retornado por [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md).  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)