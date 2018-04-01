---
title: IDebugField::Equal | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f6cba643f6d1b0f5f1d1c9fff23c8636bd12caca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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