---
title: IDebugFunctionObject::CreateArrayObject | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5dfe24252ce2ce51ff86fa680d94964b86d09365
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Cria um objeto de matriz. Essa matriz pode conter um primitivo ou valores da instância do objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateArrayObject(   
   OBJECT_TYPE    ot,  
   IDebugField*   pClassField,  
   DWORD          dwRank,  
   DWORD          dwDims[],  
   DWORD          dwLowBounds[],  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateArrayObject(  
   enum_OBJECT_TYPE ot,   
   IDebugField      pClassField,   
   uint             dwRank,   
   uint[]           dwDims,   
   uint[]           dwLowBounds,   
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ot`  
 [in] Especifica um valor a partir de [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) enumeração que indica o tipo do novo objeto de matriz.  
  
 `pClassField`  
 [in] Um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que representa a classe de um objeto, se a criação de uma matriz de objetos valores de instância. Se criar uma matriz de objetos primitivo, este parâmetro é um valor nulo.  
  
 `dwRank`  
 [in] A classificação ou o número de dimensões da matriz.  
  
 `dwDims`  
 [in] Os tamanhos de cada dimensão da matriz.  
  
 `dwLowBounds`  
 [in] A origem de cada dimensão (normalmente 0 ou 1).  
  
 `ppObject`  
 [out] Retorna um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto que representa a matriz recém-criada. Isso é realmente uma [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) objeto.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Chame esse método para criar um objeto que representa um parâmetro de matriz para a função que é representada pelo [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)