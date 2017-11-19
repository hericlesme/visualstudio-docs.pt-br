---
title: IDebugObject::GetSize | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject::GetSize
helpviewer_keywords: IDebugObject::GetSize method
ms.assetid: 89af423b-36eb-479d-b2de-2693455eca15
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab3903526ed9dc8e516520603966ea1936e46fbe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugobjectgetsize"></a>IDebugObject::GetSize
Obtém o tamanho do objeto em bytes.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetSize(   
   UINT* pnSize  
);  
```  
  
```csharp  
int GetSize(  
   out uint pnSize  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pnSize`  
 [out] Retorna o tamanho em bytes.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Use o [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md) método para recuperar o valor como uma sequência de bytes.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)