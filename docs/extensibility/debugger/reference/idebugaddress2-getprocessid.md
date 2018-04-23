---
title: IDebugAddress2::GetProcessID | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fbe84371deb7306300c69f4890398fd43c3061f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
Recupera a ID do processo que possui o objeto representado por esse [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) interface.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetProcessID (  
   DWORD* pProcID  
);  
```  
  
```csharp  
int GetProcessID (  
   out uint pProcID  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pProcID`  
 [out] A ID de processo.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)