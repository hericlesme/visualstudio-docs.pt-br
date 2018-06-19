---
title: IDebugArrayField::GetNumberOfElements | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayField::GetNumberOfElements
helpviewer_keywords:
- IDebugArrayField::GetNumberOfElements method
ms.assetid: a1961ef3-d69d-4022-b8c9-b9cfb9811345
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 16606683b516ab87c4b2b03a2aac987ae98af583
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31098674"
---
# <a name="idebugarrayfieldgetnumberofelements"></a>IDebugArrayField::GetNumberOfElements
Obtém o número de elementos na matriz.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetNumberOfElements(   
   DWORD* pdwNumElements  
);  
```  
  
```csharp  
int GetNumberOfElements(  
   out uint pdwNumElements  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwNumElements`  
 [out] Retorna o número de elementos na matriz.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O valor retornado é o número total de elementos na matriz, independentemente do número de dimensões.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)