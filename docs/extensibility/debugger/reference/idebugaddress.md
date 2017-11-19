---
title: IDebugAddress | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAddress
helpviewer_keywords: IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9f009002e9c454b1e10cac13c297e067da9c44ff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugaddress"></a>IDebugAddress
Essa interface representa o endereço de um item. Ele é retornado pelo manipulador de símbolo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugAddress : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um provedor de símbolo implementa essa interface para representar um endereço de um objeto.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Muitos métodos em interfaces de muitos retornam a esta interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem Vtable  
 Essa interface implementa o método a seguir:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Recupera um [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) estrutura que descreve um objeto e seu local.|  
  
## <a name="remarks"></a>Comentários  
 O provedor de símbolo retorna essa interface para representar um objeto e seu local dentro de um escopo específico (por exemplo, função, método ou classe). Essa interface é retornado do e passado para vários métodos do provedor de símbolo e expressão avaliador. Normalmente, o provedor de símbolo é a única entidade que precisa interpretar o conteúdo desta interface.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de provedor de símbolo](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)