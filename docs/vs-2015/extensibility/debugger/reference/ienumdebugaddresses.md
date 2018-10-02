---
title: IEnumDebugAddresses | Microsoft Docs
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
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: db0104485d960cfbeedc257c1a47ad627776dc03
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47468113"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IEnumDebugAddresses](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugaddresses).  
  
Essa interface representa uma coleção de objetos que implementam o [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Essa interface é implementada pelo provedor de símbolo para fornecer conjuntos de objetos que implementam o [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface. Observe que isso não é uma enumeração COM padrão devido à presença do [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) método.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é retornada por [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) e [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 Essa interface implementa os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Avançar](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Recupera o próximo conjunto de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objetos da enumeração.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Ignora um número especificado de entradas.|  
|[Reiniciar](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Redefine a enumeração para a primeira entrada.|  
|[Clonar](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Recupera uma cópia da enumeração atual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Recupera o número de entradas na enumeração.|  
  
## <a name="remarks"></a>Comentários  
 Normalmente, essa interface é usada pelo mecanismo de depuração para ajudar a determinar o endereço apropriado para dar ao avaliador de expressão.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)

