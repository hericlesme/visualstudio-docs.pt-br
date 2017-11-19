---
title: IDebugSymbolProvider::GetNamespacesUsedAtAddress | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugSymbolProvider::GetNamespacesUsedAtAddress
helpviewer_keywords: IDebugSymbolProvider::GetNamespacesUsedAtAddress method
ms.assetid: 392de54b-9af0-4567-953b-1b41acd1e05c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ca03fd4430c3cfcb9474cfd4c420ec5ab560aa94
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugsymbolprovidergetnamespacesusedataddress"></a>IDebugSymbolProvider::GetNamespacesUsedAtAddress
Esse método cria um enumerador para namespaces associado ao endereço de depuração.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetNamespacesUsedAtAddress(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int GetNamespacesUsedAtAddress(  
   IDebugAddress        pAddress,  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pAddress`  
 [in] O endereço de depuração.  
  
 `ppEnum`  
 [out] Retorna um [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) enumerador para os namespaces.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Pode haver vários namespaces associados com um endereço de depuração fornecido, por exemplo, aninhada namespaces ou vários `using` instruções.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)