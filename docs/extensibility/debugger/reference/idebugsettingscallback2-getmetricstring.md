---
title: IDebugSettingsCallback2::GetMetricString | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugSettingsCallback2::GetMetricString
- GetMetricString
ms.assetid: ecc875a2-8ac6-444c-a839-5191a780fd6b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bbb7de4157d991355f7ae3b0d5b6dcd27e374a1e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugsettingscallback2getmetricstring"></a>IDebugSettingsCallback2::GetMetricString
Recupera a cadeia de caracteres do valor da métrica recebe seu nome.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMetricString(  
    LPCWSTR pszType,  
    REFGUID guidSection,  
    LPCWSTR pszMetric,  
    BSTR*   pbstrValue  
);  
```  
  
```csharp  
private int GetMetricString(  
    string     pszType,  
    ref Guid   guidSection,  
    string     pszMetric,  
    out string pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszType`  
 [in] Tipo da métrica.  
  
 `guidSection`  
 [in] Identificador exclusivo da seção.  
  
 `pszMetric`  
 [in] Nome da métrica.  
  
 `pbstrValue`  
 [out] Retorna a cadeia de caracteres do valor da métrica.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)