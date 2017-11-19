---
title: IDebugAddress2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAddress2
helpviewer_keywords: IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 13161c2be23d2eec6f1d91fd59fc465cbc59a510
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugaddress2"></a>IDebugAddress2
Essa interface fornece acesso para a ID do processo que possui o objeto cujo endereço é representado por esta interface.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugAddress2 : IDebugAddress  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um provedor de símbolo implementa essa interface no mesmo objeto que implementa o [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface. Essa interface fornece acesso para a ID do processo que possui o objeto que está relacionado a esse endereço.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Use [QueryInterface](/cpp/atl/queryinterface) para obter essa interface do [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos em vtable ordem  
 Além dos métodos herdados da [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface, essa interface implementa o método a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|Recupera a ID do processo que possui o objeto representado por esta interface.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de provedor de símbolo](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)