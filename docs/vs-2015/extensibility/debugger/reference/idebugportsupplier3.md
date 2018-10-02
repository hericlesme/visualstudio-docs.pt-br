---
title: IDebugPortSupplier3 | Microsoft Docs
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
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 14a4e9f704cc5a863030ae6041f3d93276ecf18e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47473499"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugPortSupplier3](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportsupplier3).  
  
Essa interface permite que um chamador determinar se um fornecedor de porta pode preservar as portas (gravá-los em disco) entre as invocações do depurador e, em seguida, obter uma lista dessas portas preservado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um fornecedor de porta personalizada implementa essa interface para dar suporte a persistir ou salvar informações de porta para o disco. Esta interface deve ser implementada no mesmo objeto como o [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chame [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) sobre o `IDebugPortSupplier2` interface para obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 Além dos métodos herdados do [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) interface, essa interface dá suporte para o seguinte:  
  
|Método|Descrição|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Retorna se o fornecedor de porta pode persistir portas (gravando-os em disco) entre as invocações do depurador.|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Retorna um objeto que pode ser usado para enumerar todas as portas que foram gravados no disco por esse fornecedor de porta.|  
  
## <a name="remarks"></a>Comentários  
 Se um fornecedor de porta pode persistir as portas entre invocações, ele deve implementar essa interface. As portas devem ser carregadas quando o fornecedor de porta é instanciado e gravado em disco quando o fornecedor de porta é destruído.  
  
 Normalmente, um mecanismo de depuração não interage com um fornecedor de porta e não terá nenhum uso para essa interface.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Principais Interfaces](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)

