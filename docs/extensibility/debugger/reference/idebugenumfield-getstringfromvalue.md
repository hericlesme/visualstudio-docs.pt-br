---
title: IDebugEnumField::GetStringFromValue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a0b7ac4f7cde93d4637906202f7b4c643750d8e0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugenumfieldgetstringfromvalue"></a>IDebugEnumField::GetStringFromValue
Esse método obtém o nome da constante de enumeração recebe seu valor.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetStringFromValue(  
   ULONGLONG value,  
   BSTR*     pbstrValue  
);  
```  
  
```csharp  
int GetStringFromValue(  
   ulong      value,  
   out string pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `value`  
 [in] O valor para o qual obter o nome da enumeração constante.  
  
 `pbstrValue`  
 [out] Retorna o nome da constante de enumeração.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna `S_FALSE` se o valor sem nome associado ou retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Se houver mais de um nome de associado com o mesmo valor, o nome definido na enumeração será retornado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)