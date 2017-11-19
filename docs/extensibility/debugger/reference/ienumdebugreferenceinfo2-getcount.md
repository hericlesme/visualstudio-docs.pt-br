---
title: IEnumDebugReferenceInfo2::GetCount | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugReferenceInfo2::GetCount
helpviewer_keywords: IEnumDebugReferenceInfo2::GetCount
ms.assetid: e62706e0-d2cd-48fb-8fdf-444463c651ab
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6caaf793b9449b238c1edcbdd28942068adf753b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugreferenceinfo2getcount"></a>IEnumDebugReferenceInfo2::GetCount
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
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)