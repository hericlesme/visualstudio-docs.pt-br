---
title: IEnumDebugPorts2::Skip | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugPorts2::Skip
helpviewer_keywords:
- IEnumDebugPorts2::Skip
ms.assetid: a837383f-7b39-4e06-b336-f1715b073dbe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5369b4fa47eb31c7f40c0584b7b1c060ab41b119
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126669"
---
# <a name="ienumdebugports2skip"></a>IEnumDebugPorts2::Skip
Ignora o número especificado de elementos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `celt`  
 [in] Número de elementos a serem ignorados.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se `celt` for maior que o número de elementos restantes; caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Se `celt` Especifica um valor maior que o número de elementos restantes, a enumeração está definida para o fim e `S_FALSE` é retornado.  
  
## <a name="see-also"></a>Consulte também  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)