---
title: IDebugArrayObject::GetRank | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayObject::GetRank
helpviewer_keywords: IDebugArrayObject::GetRank method
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8a3da9ad46a39e0324c71a205b005be61298292f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugarrayobjectgetrank"></a>IDebugArrayObject::GetRank
Obtém a classificação da matriz, ou seja, o número de dimensões.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```csharp  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwRank`  
 [out] Retorna a classificação.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Use o [GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md) método para recuperar o tamanho de cada dimensão do objeto de matriz.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)