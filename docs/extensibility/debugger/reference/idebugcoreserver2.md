---
title: IDebugCoreServer2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
caps.latest.revision: 14
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 31961d62c2ef7a253a16a5384dfa6b5e69209a97
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
Essa interface é usada para representar e obter informações de um servidor em um computador na rede.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugCoreServer2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O Visual Studio implementa essa interface para representar um servidor. Cada instância do Visual Studio cria uma instância desta interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Um fornecedor de porta personalizada recebe essa interface em uma chamada para [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md).  
  
 Um mecanismo de depuração pode obter essa interface indiretamente por meio de uma chamada para [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) (que retorna [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md), uma interface que é derivada de `IDebugCoreServer2`).  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugCoreServer2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Obtém o nome e os atributos de uma máquina.|  
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Obtém o nome de uma máquina.|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Obtém um fornecedor de porta que existe em um computador.|  
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Obtém uma porta que já existe em um computador.|  
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Cria um enumerador para todas as portas em um computador.|  
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Cria um enumerador para todos os fornecedores de porta em um computador.|  
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Obtém os utilitários de máquina para uma máquina.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface também é usada pelo Visual Studio para procurar processos em execução em computadores na rede.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)