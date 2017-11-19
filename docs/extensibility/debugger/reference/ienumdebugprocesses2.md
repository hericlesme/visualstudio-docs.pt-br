---
title: IEnumDebugProcesses2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugProcesses2
helpviewer_keywords: IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6e5be156ec0a30f736b96cfe6451b893dfb8eacf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
Essa interface enumera os processos em execução em uma porta de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IEnumDebugProcesses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um fornecedor de porta personalizada implementa essa interface para fornecer uma lista de processos em execução em uma porta.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamadas do Visual Studio [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) para obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 A tabela a seguir mostra os métodos de `IEnumDebugProcesses2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Avançar](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Recupera um número especificado de processos em uma sequência de enumeração.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Ignora um número especificado de processos em uma sequência de enumeração.|  
|[Redefinir](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Redefine uma sequência de enumeração para o início.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração do enumerador atual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Obtém o número de processos em um enumerador.|  
  
## <a name="remarks"></a>Comentários  
 O Visual Studio usa essa interface para preencher o **processos** janela.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)