---
title: IEnumDebugProcesses2 | Microsoft Docs
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
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 802dfd38f3a2765c876a5e026c21a9028fb6642e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475830"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IEnumDebugProcesses2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugprocesses2).  
  
Essa interface enumera os processos em execução em uma porta de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IEnumDebugProcesses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um fornecedor de porta personalizada implementa essa interface para fornecer uma lista de processos em execução em uma porta.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamadas do Visual Studio [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) para obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IEnumDebugProcesses2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Avançar](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Recupera um número especificado de processos em uma sequência de enumeração.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Ignora um número especificado de processos em uma sequência de enumeração.|  
|[Reiniciar](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Redefine uma sequência de enumeração para o início.|  
|[Clonar](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Obtém o número de processos em um enumerador.|  
  
## <a name="remarks"></a>Comentários  
 O Visual Studio usa essa interface para preencher a **processos** janela.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Principais Interfaces](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)

