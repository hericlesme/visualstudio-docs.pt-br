---
title: IDebugDynamicField | Microsoft Docs
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
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7e975940947b68fdce34bd7d1e2e289c85914c44
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475349"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugDynamicField](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdynamicfield).  
  
Essa interface representa um tipo de uma variável.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugDynamicField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada por provedores de símbolo como uma classe base para qualquer tipo que pode ser determinada em tempo de execução. Isso é apenas para código gerenciado.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface representa uma classe base da qual as interfaces mais especializadas podem ser derivadas.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 Essa interface fornece métodos que não sejam aqueles herdados de `IDebugField`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

