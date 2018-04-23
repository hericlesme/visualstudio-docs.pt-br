---
title: IEnumDebugPorts2::GetCount | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugPorts2::GetCount
helpviewer_keywords:
- IEnumDebugPorts2::GetCount
ms.assetid: d714455c-e4fc-48dc-a6d4-7e8b5d7c1bce
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1122e791ebbf62be5262958e2995ffaa733e865e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugports2getcount"></a>IEnumDebugPorts2::GetCount
Retorna o número de elementos na enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pcelt`  
 [out] Retorna o número de elementos na enumeração.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Este método não é parte da interface habitual de enumeração COM que especifica que somente o `Next`, `Clone`, `Skip`, e `Reset` métodos precisam ser implementado.  
  
## <a name="see-also"></a>Consulte também  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)