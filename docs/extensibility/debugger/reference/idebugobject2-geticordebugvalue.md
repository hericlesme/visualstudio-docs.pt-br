---
title: IDebugObject2::GetICorDebugValue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugObject2::GetICorDebugValue
helpviewer_keywords:
- IDebugObject2::GetICorDebugValue method
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5b28e0cd6d66479479dbdb51825e0804abab06be
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobject2geticordebugvalue"></a>IDebugObject2::GetICorDebugValue
Obtém um objeto de código gerenciado que representa o valor associado a este objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppUnk`  
 [out] `IUnknown` interface que representa este alias. Essa interface pode ser consultada para o `ICorDebugValue` interface.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O `ICorDebugValue` objeto é uma interface de Common Language Runtime que representa um valor.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)