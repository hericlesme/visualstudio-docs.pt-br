---
title: IEnumCodePaths2::Next | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumCodePaths2::Next
helpviewer_keywords:
- IEnumCodePaths2::Next
ms.assetid: c7a8fe97-2abc-4cee-8aef-64f1daa93b5c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 63e13ece4b91721cb391d5f7875c2799e297068b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120771"
---
# <a name="ienumcodepaths2next"></a>IEnumCodePaths2::Next
Retorna o próximo conjunto de elementos da enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Next(  
   ULONG       celt,  
   CODE_PATH** rgelt,  
   ULONG*      pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint        celt,  
   CODE_PATH[] rgelt,  
   ref uint    pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 [in] O número de elementos para recuperar. Também especifica o tamanho máximo da `rgelt` matriz.  
  
 `rgelt`  
 [out no] Matriz de [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) elementos devem ser preenchidos.  
  
 `pceltFetched`  
 [out] Retorna o número de elementos realmente retornados em `rgelt`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se menos do que o número solicitado de elementos podem ser retornados; caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)   
 [CODE_PATH](../../../extensibility/debugger/reference/code-path.md)