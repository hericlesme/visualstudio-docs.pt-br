---
title: IEnumDebugCustomAttributes | Microsoft Docs
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
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 695fb7c68f76d4cd91c079490436b9aaf38ecd13
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47467845"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IEnumDebugCustomAttributes](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugcustomattributes).  
  
Enumera os atributos personalizados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IEnumCustomAttributes : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um provedor de símbolo implementa essa interface para dar suporte a atributos personalizados (por meio de [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) interface).  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) retorna essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IEnumDebugCustomAttributes`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Avançar](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|Recupera um número especificado de atributos personalizados em uma sequência de enumeração.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|Ignora um número especificado de atributos personalizados em uma sequência de enumeração.|  
|[Reiniciar](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|Redefine uma sequência de enumeração para o início.|  
|[Clonar](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|Obtém o número de atributos personalizados em um enumerador.|  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de provedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)

