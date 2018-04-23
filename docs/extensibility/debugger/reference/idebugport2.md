---
title: IDebugPort2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d1811ad7e46865d00eed2066d061daec78d7ab2b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugport2"></a>IDebugPort2
Essa interface representa uma porta de depuração em um computador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um fornecedor de porta personalizada implementa essa interface para representar uma porta de depuração em um computador.  
  
 Se a porta oferece suporte a eventos de porta de envio, ele deverá implementar também a <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface para oferecer suporte a um <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface que por sua vez fornece o [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamadas para [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) ou [adicionar porta](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) retornar esta interface, que representa a porta solicitada.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IDebugPort2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Retorna o nome de porta.|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Retorna o identificador de porta.|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Retorna a solicitação usada para criar uma porta (se disponível).|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Retorna o fornecedor de porta para essa porta.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Retorna uma interface para o processo recebe o identificador do processo.|  
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Enumera todos os processos em execução em uma porta.|  
  
## <a name="remarks"></a>Comentários  
 A porta local fornece acesso a todos os processos e programas em execução no computador local. Outras portas podem representar uma conexão de cabo serial para um dispositivo baseado em Windows CE ou uma conexão de rede em um computador não DCOM. O `IDebugPort2` interface é usada para localizar o nome e o identificador de uma porta, enumerar todos os processos em execução na porta e fornecer recursos para iniciar e encerrar processos na porta.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)