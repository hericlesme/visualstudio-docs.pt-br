---
title: IDebugBreakpointErrorEvent2 | Microsoft Docs
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
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 554d0768f46ef0cdff46b46ece43b8fe7a2c72e1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47476142"
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugBreakpointErrorEvent2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbreakpointerrorevent2).  
  
Essa interface informa o Gerenciador de sessão de depuração (SDM) que um ponto de interrupção pendente não pôde ser associado a um programa carregado, por causa de um aviso ou erro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugBreakpointErrorEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O DE implementa essa interface como parte de seu suporte para pontos de interrupção. O [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface deve ser implementada no mesmo objeto como essa interface (usa o SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) para acessar o `IDebugEvent2` interface).  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O DE cria e envia esse objeto de evento quando um ponto de interrupção pendente não pode ser associado ao programa que está sendo depurado. O evento é enviado usando o [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) função de retorno de chamada fornecida pelo SDM quando anexado a programa que está sendo depurado.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDebugBreakpointErrorEvent2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Obtém o [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interface que descreve o erro ou aviso.|  
  
## <a name="remarks"></a>Comentários  
 Sempre que um ponto de interrupção está associado, um evento é enviado para o SDM. Se o ponto de interrupção não pode ser associado, uma `IDebugBreakpointErrorEvent2` é enviada; caso contrário, uma [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) é enviada.  
  
 Por exemplo, quando não conseguir analisar ou avaliar a condição associada com o ponto de interrupção pendente, um aviso é enviado de que o ponto de interrupção pendente não pode ser associado no momento. Isso pode ocorrer se o código para o ponto de interrupção não tiver sido carregado ainda.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

