---
title: IDebugPortSupplier3 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortSupplier3
helpviewer_keywords: IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3bd2a46573ca655df3372c33182860cf2d4816d7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Essa interface permite que um chamador determinar se um fornecedor de porta pode preservar portas (por gravá-los em disco) entre chamadas do depurador e, em seguida, obter uma lista dessas portas preservado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um fornecedor de porta personalizada implementa essa interface para dar suporte à persistência ou salvar informações de porta para o disco. Esta interface deve ser implementada no mesmo objeto, como o [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chamar [QueryInterface](/cpp/atl/queryinterface) no `IDebugPortSupplier2` interface para obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Além dos métodos herdados da [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) interface, esta interface dá suporte para o seguinte:  
  
|Método|Descrição|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Retorna se o fornecedor de porta pode persistir portas (por gravá-los em disco) entre chamadas do depurador.|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Retorna um objeto que pode ser usado para enumerar todas as portas que foram gravadas em disco por fornecedor essa porta.|  
  
## <a name="remarks"></a>Comentários  
 Se um fornecedor de porta pode manter portas entre invocações, ele deve implementar essa interface. Portas devem ser carregadas quando o fornecedor de porta é instanciado e gravado em disco quando o fornecedor de porta é destruído.  
  
 Normalmente, um mecanismo de depuração não consegue interagir com um fornecedor de porta e não terá nenhum uso para esta interface.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)