---
title: IDebugDynamicField | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
caps.latest.revision: 7
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d1fdd5e0eeb7aeb88b999e72dac875a41c0e0b03
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Essa interface representa um tipo de uma variável.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugDynamicField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada pelos provedores de símbolo como uma classe base para qualquer tipo que pode ser determinada em tempo de execução. Isso é somente código gerenciado.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface representa uma classe base da qual mais especializadas de interfaces podem ser derivadas.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Esta interface não fornece qualquer métodos diferentes aquelas herdadas do `IDebugField`.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de provedor de símbolo](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)