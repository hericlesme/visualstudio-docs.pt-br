---
title: IDebugProcessQueryProperties | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 542933f414e4ca95da181d26d2cc49c582e553c0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47463023"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugProcessQueryProperties](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocessqueryproperties).  
  
Essa interface é implementada por uma interface de extensão [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) implementadores. Ele permite que o implementador obter informações sobre o ambiente do processo de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Implemente essa interface para obter informações sobre o ambiente de execução de um processo de depuração.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDebugProcessQueryProperties`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Consultas para um valor da propriedade.|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Consultas de valores de propriedade.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface é implementada raramente.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Principais Interfaces](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)

