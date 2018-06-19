---
title: IDebugField::Equal | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b2d195c28123cc786c9a5a97add98b7f67d499b7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121870"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Este método compara esse campo com o campo especificado para igualdade.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```csharp  
int Equal(  
   IDebugField pField  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pField`  
 [in] O campo a ser comparado com este.  
  
## <a name="return-value"></a>Valor de retorno  
 Se os campos são os mesmos, retornará `S_OK`. Se os campos são diferentes, retorna `S_FALSE.` caso contrário, retornará um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)