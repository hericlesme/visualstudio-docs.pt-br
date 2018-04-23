---
title: IDebugArrayObject::GetDimensions | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5a20073a19f785d30b0fcd0a7f126919371e722c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
Obtém as dimensões da matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```csharp  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwCount`  
 [in] O número de dimensões para recuperar.  
  
 `dwDimensions`  
 [out no] Uma matriz que é preenchida com os tamanhos de cada dimensão. `dwCount` Especifica o tamanho máximo da `dwDimensions` matriz.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Uma matriz multidimensional pode ter tamanhos diferentes para cada dimensão. Por exemplo, dada a matriz tridimensional `myarray[3][2][6]`, esse método retorna 3, 2 e 6 de `dwDimensions` parâmetro nessa ordem.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)