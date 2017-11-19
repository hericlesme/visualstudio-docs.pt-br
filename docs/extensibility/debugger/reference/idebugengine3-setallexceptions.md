---
title: IDebugEngine3::SetAllExceptions | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine3::SetAllExceptions
helpviewer_keywords: IDebugEngine3::SetAllExceptions
ms.assetid: 8f03a6ac-a854-42f7-933c-a2df1b351975
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 33801c7228e9f4b43c76ef3f29f26631bdad5edf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine3setallexceptions"></a>IDebugEngine3::SetAllExceptions
Esse método define o estado de todas as exceções pendentes.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetAllExceptions(  
   EXCEPTION_STATE dwState  
);  
```  
  
```csharp  
int SetAllExceptions(  
   enum_EXCEPTION_STATE dwState  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwState`  
 [in] Uma da [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) valores.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retornará o código de erro.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)