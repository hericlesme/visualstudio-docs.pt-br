---
title: IDebugAlias::GetObject | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAlias::GetObject
helpviewer_keywords: IDebugAlias::GetObject method
ms.assetid: 97bc3af6-6e55-4940-8a6d-692c61257806
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e1b96592e54e36d63da124e1a239430995bfaec5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugaliasgetobject"></a>IDebugAlias::GetObject
Obtém o objeto que é este alias.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetObject(  
   IDebugObject2** ppObject  
);  
```  
  
```csharp  
int GetObject(  
   Out IDebugObject2 ppObject  
)  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppObject`  
 [out] O [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) representa este alias.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará S_OK; Caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)