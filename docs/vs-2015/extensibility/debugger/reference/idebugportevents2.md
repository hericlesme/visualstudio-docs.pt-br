---
title: IDebugPortEvents2 | Microsoft Docs
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
- IDebugPortEvents2
helpviewer_keywords:
- IDebugPortEvents2 interface
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3eb6208d815e4951bd916d014cddfdda34a8e589
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466145"
---
# <a name="idebugportevents2"></a>IDebugPortEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugPortEvents2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportevents2).  
  
Essa interface notifica um ouvinte (normalmente o sessão Gerenciador de depuração [SDM] ou um mecanismo de depuração) do programa e o processo de criação e destruição em uma porta específica. Essas informações podem ser usadas para apresentar uma exibição em tempo real dos processos e programas em execução na porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Normalmente, o Visual Studio implementa essa interface para receber notificações sobre a criação do programa e a destruição. Um mecanismo de depuração também pode implementar essa interface para monitorar esses eventos de porta.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Todos os [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfaces podem ser consultadas para um <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface. Em seguida, a <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> método para `IDebugPortEvents2` é chamado na <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface para obter um <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface. Por fim, o <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> método no <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface é chamado para enviar os eventos por meio de [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md) método.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra o método de `IDebugPortEvents2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)|Envia os eventos que descrevem a criação e destruição de processos e programas na porta.|  
  
## <a name="remarks"></a>Comentários  
 `IDebugPortEvents2` também é usado pelo SDM para depurar programas que são executados em um processo que já está sendo depurado.  
  
 Eventos de porta são passados para o SDM por esta interface.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Principais Interfaces](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)

