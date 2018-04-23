---
title: IDebugArrayObject::GetElement | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e2e10eced58835044220da0650712dacb131ada3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
Obtém um elemento da matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetElement(   
   DWORD          dwIndex,  
   IDebugObject** ppElement  
);  
```  
  
```csharp  
int GetElement(  
   [In] uint dwIndex,   
   out IDebugObject ppElement  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwIndex`  
 [in] O índice do elemento.  
  
 `ppElement`  
 [out] Retorna um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface que representa o elemento.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método considera todos os elementos de um objeto de matriz como uma matriz unidimensional, mesmo se o objeto de matriz é multidimensional. Por exemplo, dada a matriz `myarray[3][2][6]` e um `dwIndex` parâmetro de 20, esse método retornará o elemento de `myarray[1][1][2]`e um `dwIndex` parâmetro 21 retornará o elemento de `myarray[1][1][3]`. Use o [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) método para determinar o número total de elementos na matriz.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)