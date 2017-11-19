---
title: IDebugDynamicField | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDynamicField
helpviewer_keywords: IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5bb632d2ca51090f88b33ea6a8365fa9ac13ba9f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
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