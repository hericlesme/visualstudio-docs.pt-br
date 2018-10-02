---
title: IDebugProcess2 | Microsoft Docs
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
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cfb5a4fbd1c1e3b164b3e690da07136099711607
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47468369"
---
# <a name="idebugprocess2"></a>IDebugProcess2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugProcess2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocess2).  
  
Essa interface representa um processo em execução em uma porta. Se a porta é a porta local, em seguida, `IDebugProcess2` normalmente representa um processo físico no computador local.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada por um fornecedor de porta personalizada para gerenciar os programas como um grupo. Esta interface deve ser implementada pelo fornecedor de porta.  
  
 Um mecanismo de depuração também implementa essa interface se ele dá suporte a iniciar um programa por meio [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é chamada principalmente pelo Gerenciador de depuração de sessão (SDM) para interagir com um grupo de programas identificado nesse processo.  
  
 Chame [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) ou [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) para obter essa interface. Essa interface também é retornada ao chamar `IDebugEngineLaunch2::LaunchSuspended`.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDebugProcess2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Obtém uma descrição do processo.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Enumera os programas que estão contidos neste processo.|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Obtém o título, o nome amigável ou o nome de arquivo do processo.|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Obtém a instância de um servidor de máquina, que esse processo está em execução no.|  
|[Terminar](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Encerra o processo.|  
|[Anexar](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Anexa ao processo.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Determina se o SDM poderá desanexar o processo.|  
|[Desanexar](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Desanexa o depurador do processo.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Obtém o identificador de processo do sistema.|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Obtém um identificador global exclusivo para esse processo.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [PRETERIDO]|Obtém o nome da sessão que é o processo de depuração.<br /><br /> [PRETERIDO. DEVE SEMPRE RETORNAR `E_NOTIMPL`.]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Enumera os threads em execução no processo.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Solicita que o próximo programa executando código em parar este processo.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Obtém a porta que esse processo está sendo executado.|  
  
## <a name="remarks"></a>Comentários  
 Uma `IDebugProcess2` contém um ou mais [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaces.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Principais Interfaces](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [Avançar](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

