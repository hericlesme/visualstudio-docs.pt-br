---
title: IDebugEngine2::SetRegistryRoot | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::SetRegistryRoot
helpviewer_keywords:
- IDebugEngine2::SetRegistryRoot
ms.assetid: d0d81202-8a4a-4bc3-b297-30a047c5ec60
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 606ddb5380da2bfe0c75d20bc70bf0da911ea4e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengine2setregistryroot"></a>IDebugEngine2::SetRegistryRoot
Define a raiz do registro para o mecanismo de depuração (DE).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetRegistryRoot(   
   LPCOLESTR pszRegistryRoot  
);  
```  
  
```csharp  
int SetRegistryRoot(   
   string pszRegistryRoot  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pszRegistryRoot`  
 [in] A raiz do registro para usar.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Esse método permite que [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] para especificar uma raiz de registro alternativo que o DE deve usar para obter as configurações do registro; por exemplo, "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp".  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)