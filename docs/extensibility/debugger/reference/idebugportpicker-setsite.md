---
title: IDebugPortPicker::SetSite | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 54286ded44f6acf44033c2fa5e2227ccaa688a64
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
Define o provedor de serviços.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetSite(  
   IServiceProvider * pSP  
);  
```  
  
```csharp  
public int SetSite(  
   IServiceProvider pSP  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pSP`  
 [in] Referência para a interface do provedor de serviço.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método será chamado antes de quaisquer outros métodos são chamados.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)