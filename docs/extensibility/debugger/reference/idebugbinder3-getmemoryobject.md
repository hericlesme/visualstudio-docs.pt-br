---
title: IDebugBinder3::GetMemoryObject | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder3::GetMemoryObject
helpviewer_keywords: IDebugBinder3::GetMemoryObject method
ms.assetid: 71d959c7-45df-485f-b0ee-f1c0439d54fb
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3c9a031ec057194cbadcaf863c328cdfac9b4931
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugbinder3getmemoryobject"></a>IDebugBinder3::GetMemoryObject
Esse método retorna um objeto de memória que representa a memória associado a este objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMemoryObject(  
   IDebugField*   pField,  
   UINT64         uConstant,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int GetMemoryObject(  
   IDebugField      pField,  
   long             uConstant,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pField`  
 [in] Especifica qual campo para obter o objeto de memória para.  
  
 `uConstant`  
 [in] Representa um valor para um valor constante ou um endereço de memória.  
  
 `ppObject`  
 [out] Um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa a memória associado a este objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)