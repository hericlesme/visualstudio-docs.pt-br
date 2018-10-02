---
title: IDebugEngine2 | Microsoft Docs
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
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 38b3b6f9ba7a88d1babc60a092e4703b99d20b64
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467151"
---
# <a name="idebugengine2"></a>IDebugEngine2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugEngine2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugengine2).  
  
Essa interface representa um mecanismo de depuração (DES). Ele é usado para gerenciar vários aspectos de uma sessão de depuração, desde a criação de pontos de interrupção para definir e apagar as exceções.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada por uma personalizado DE gerenciar a depuração de programas. Esta interface deve ser implementada por DE.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é chamada pelo Gerenciador de depuração (SDM) para gerenciar a sessão de depuração, incluindo gerenciamento de exceções, criando pontos de interrupção e respondendo a eventos síncronos enviados pelo DE sessão.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDebugEngine2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Cria um enumerador para todos os programas sendo depurado por um DE.|  
|[Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Anexa a DE um programa.|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Cria um ponto de interrupção pendente em DE.|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Especifica como o DE deve lidar com uma determinada exceção.|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Remove a exceção especificada, para que ele não é tratado pelo mecanismo de depuração.|  
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Remove a lista de exceções, que o IDE foi definido para um idioma ou a arquitetura de tempo de execução específica.|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Obtém o GUID DE.|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informa a DE que o programa especificado foi encerrado atypically e que o DE deve limpar todas as referências para o programa e enviar um programa de destruir o evento.|  
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Chamado pelo SDM para indicar que um evento de depuração síncrona, enviado anteriormente pelo DE para o SDM, foi recebido e processado.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Define a localidade de.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Define a raiz do registro atualmente em uso por DE.|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Define uma métrica.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Solicitações que todos os programas sendo depurados por este DE parar a execução na próxima vez que um dos seus threads tenta ser executado.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)

