---
title: IDebugObject2::CreateAlias | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject2::CreateAlias
helpviewer_keywords: IDebugObject2::CreateAlias method
ms.assetid: 54a05920-5d13-4f67-962b-d1a7f013dff9
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 33e3acc46fab56a1096c6537d5b5ee5569e09063
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugobject2createalias"></a>IDebugObject2::CreateAlias
Cria uma ID exclusiva ou um alias para esse objeto ou retorna um alias existente.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateAlias(  
   IDebugAlias** ppAlias  
);  
```  
  
```csharp  
int CreateAlias(  
   out IDebugAlias ppAlias  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppAlias`  
 [out] O alias do novo (ou existente).  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Um alias é um rótulo que representa um objeto específico, enquanto o objeto está na memória.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)