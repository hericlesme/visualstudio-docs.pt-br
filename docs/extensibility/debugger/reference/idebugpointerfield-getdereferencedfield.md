---
title: IDebugPointerField::GetDereferencedField | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPointerField::GetDereferencedField
helpviewer_keywords: IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 35081931fcb87c73ca6643002a09b43c3ab674b9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
Esse método retorna o tipo de objeto para o qual este objeto de ponteiro aponta.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetDereferencedField(  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetDereferencedField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppField`  
 [out] Retorna um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que descreve o tipo de objeto de destino.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Se, por exemplo, o [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) objeto aponta para um número inteiro, o [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) tipo retornado por este método descreve que tipo de inteiro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)