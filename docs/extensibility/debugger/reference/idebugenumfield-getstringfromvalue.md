---
title: IDebugEnumField::GetStringFromValue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEnumField::GetStringFromValue
helpviewer_keywords:
- IDebugEnumField::GetStringFromValue method
ms.assetid: 5f95fd0c-fdce-497f-9f54-2ad8749494e9
caps.latest.revision: 5
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 695c35e6d849806911aaf9cb293b53e66dbbca0e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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