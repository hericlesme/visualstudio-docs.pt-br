---
title: IEnumDebugFields::GetCount | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugFields::GetCount
helpviewer_keywords: IEnumDebugFields::GetCount method
ms.assetid: 3f471b40-4db3-49f7-b504-58b2476eef74
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0dbbafda528d88f84f9796037faa6587e8789fcc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugfieldsgetcount"></a>IEnumDebugFields::GetCount
Esse método retorna o número de elementos na enumeração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCount(  
   [out] ULONG* pcelt  
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
 Este método não é parte da interface habitual de enumeração COM que especifica que somente Avançar, Clone, Skip e redefinição precisam ser implementado.  
  
## <a name="see-also"></a>Consulte também  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)