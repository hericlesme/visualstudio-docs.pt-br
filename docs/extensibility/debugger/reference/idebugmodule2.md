---
title: IDebugModule2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4ffa4044e6490f8de8228541787b7bf8ab80285a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmodule2"></a>IDebugModule2
Essa interface representa um módulo — ou seja, uma unidade executável de um programa, como uma DLL.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugModule2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração (DE) implementa essa interface para representar um módulo e fornecer acesso a informações sobre o que o módulo.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Uma chamada para [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) retorna essa interface. O envia do [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) interface para o Gerenciador de depuração de sessão (SDM) usando o [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) método.  
  
 Essa interface também pode ser retornada em uma [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) estrutura (que é retornado por uma chamada para [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).  
  
 [Próxima](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) também retorna essa interface ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) retorna o [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) interface).  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugModule2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Obtém o [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) que descreve este módulo.|  
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|OBSOLETO. NÃO USE. Recarrega os símbolos para esse módulo.|  
  
## <a name="remarks"></a>Comentários  
 Informações de módulo podem ser exibidas no **módulos** janela do IDE.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)