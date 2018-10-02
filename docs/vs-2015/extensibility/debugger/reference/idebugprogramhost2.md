---
title: IDebugProgramHost2 | Microsoft Docs
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
- IDebugProgramHost2
helpviewer_keywords:
- IDebugProgramHost2 interface
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd8e0b54765f20dce21eae135b0942547f967836
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467666"
---
# <a name="idebugprogramhost2"></a>IDebugProgramHost2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugProgramHost2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprogramhost2).  
  
Essa interface fornece informações de host (processo) sobre um programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugProgramHost2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O mecanismo de depuração implementa essa interface no mesmo objeto como o [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface para fornecer informações sobre o processo de hospedagem. Esta é uma interface opcional.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chame [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) em um `IDebugProgram2` interface para obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDebugProgramHost2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|Obtém o título, o nome amigável ou o nome do arquivo do processo de hospedagem desse programa.|  
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|Obtém o identificador de processo do processo de hospedagem desse programa.|  
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|Obtém o nome do computador que o processo de hospedagem desse programa está em execução.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Principais Interfaces](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

