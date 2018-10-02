---
title: IDebugBinder::ResolveRuntimeType | Microsoft Docs
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
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e1ac794f7ba3cc3b47cf96dacde850845fd07c9e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47464376"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugBinder::ResolveRuntimeType](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbinder-resolveruntimetype).  
  
Este método determina o tipo de tempo de execução de um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT ResolveRuntimeType(   
   IDebugObject* pObject,  
   IDebugField** ppResolved  
);  
```  
  
```csharp  
int ResolveRuntimeType(  
   IDebugObject     pObject,   
   out IDebugField  ppResolved  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pObject`  
 [in] O [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) sejam resolvidos.  
  
 `ppResolved`  
 [out] Retorna o tipo do objeto como um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O tipo de tempo de execução de um objeto não é sempre conhecido em tempo de compilação. Por exemplo, usando o polimorfismo, um argumento pode ser passado para uma função como sua classe base, como uma classe de botão. O argumento real pode ser uma classe derivada, como uma classe de botão de rádio.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

