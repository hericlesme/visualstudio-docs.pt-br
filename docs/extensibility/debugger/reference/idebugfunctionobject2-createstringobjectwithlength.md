---
title: IDebugFunctionObject2::CreateStringObjectWithLength | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CreateStringObjectWithLength
- IDebugFunctionObject2::CreateStringObjectWithLength
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 78b5f21a2b2f018c4eb35007cdfd2aa4f67b5ebf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfunctionobject2createstringobjectwithlength"></a>IDebugFunctionObject2::CreateStringObjectWithLength
Cria um objeto de cadeia de caracteres que tem o comprimento especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT CreateStringObjectWithLength (  
   LPCOLESTR      pcstrString,  
   UINT           uiLength,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateStringObjectWithLength (  
   string           pcstrString,  
   uint             uiLength,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pcstrString`  
 [in] O valor de cadeia de caracteres para o objeto de cadeia de caracteres.  
  
 `uiLength`  
 [in] O comprimento da cadeia de caracteres em bytes.  
  
 `ppObject`  
 [out] Retorna um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto que representa o objeto de cadeia de caracteres criada recentemente.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)