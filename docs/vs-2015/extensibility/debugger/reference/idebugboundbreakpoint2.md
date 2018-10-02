---
title: IDebugBoundBreakpoint2 | Microsoft Docs
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
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8ac6400c9a56ba0b24ee1b6f5342e8ed2038deea
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47476126"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugBoundBreakpoint2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugboundbreakpoint2).  
  
Essa interface representa um ponto de interrupção que está associado a um local de código.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugBoundBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DES) implementa essa interface como parte de seu suporte para pontos de interrupção.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Uma chamada para [associar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) cria essa interface. Chamadas para [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) e [próxima](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) também pode obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDebugBoundBreakpoint2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Obtém o ponto de interrupção pendente da qual o ponto de interrupção associado especificado foi criado.|  
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Obtém o estado deste ponto de interrupção associada.|  
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Obtém a contagem de ocorrências atual para este ponto de interrupção associado.|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Obtém a resolução de ponto de interrupção que descreve este ponto de interrupção.|  
|[Habilitar](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Habilita ou desabilita o ponto de interrupção.|  
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Define a contagem de ocorrências para esse ponto de interrupção associada.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Define ou altera a condição associada a este ponto de interrupção associado.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Define ou alterar a contagem de passagem associada a este ponto de interrupção associado.|  
|[Excluir](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Exclui o ponto de interrupção.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)   
 [Avançar](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)   
 [Associar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)

