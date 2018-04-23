---
title: IDebugExceptionEvent2::GetExceptionDescription | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExceptionEvent2::GetExceptionDescription
helpviewer_keywords:
- IDebugExceptionEvent2::GetExceptionDescription
ms.assetid: d07d458f-5729-47e4-9b77-1bd59c61a75a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 35baacc0eca2919e12a9056b902ab551e7f824bd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexceptionevent2getexceptiondescription"></a>IDebugExceptionEvent2::GetExceptionDescription
Obtém uma descrição pode ser exibida da exceção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetExceptionDescription(   
   BSTR* pbstrDescription  
);  
```  
  
```csharp  
int GetExceptionDescription(   
   out string pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pbstrDescription`  
 [out] Retorna uma descrição pode ser exibida da exceção.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 A cadeia de caracteres retornada deste método é geralmente o nome da exceção e é mostrada no **saída** janela quando a exceção ocorrer.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)