---
title: IDebugObject::IsEqual | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject::IsEqual
helpviewer_keywords: IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2af7ef11a142442b97dbb5d6a4d0545bf118da39
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Compara a um objeto com esse objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT IsEqual(   
   IDebugObject* pObject,  
   BOOL*         pfIsEqual  
);  
```  
  
```csharp  
int IsEqual(  
   IDebugObject pObject,  
   out int      pfIsEqual  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pObject`  
 [in] Um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto que representa o objeto a ser comparado.  
  
 `pfIsEqual`  
 [out] Retorna diferente de zero (`TRUE`) se os valores dos objetos forem iguais; caso contrário, retorna zero (`FALSE`).  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Normalmente, esse método pode comparar os endereços dos valores representados pelo `pObject` parâmetro e isso [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto; se os endereços são iguais e, em seguida, os objetos podem ser considerados iguais.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)