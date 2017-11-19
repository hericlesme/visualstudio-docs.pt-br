---
title: IDebugBinder::ResolveRuntimeType | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder::ResolveRuntimeType
helpviewer_keywords: IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3f682b676a793a9a8a29e31f29920b212d127aff
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
Este método determina o tipo de tempo de execução de um objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O tipo de tempo de execução de um objeto não é sempre conhecido em tempo de compilação. Por exemplo, usando polimorfismo, um argumento pode ser passado para uma função como sua classe base, como uma classe de botão. O argumento pode ser uma classe derivada, como uma classe de botão de opção.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)