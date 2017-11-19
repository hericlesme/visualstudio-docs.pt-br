---
title: IDebugDefaultPort2::GetServer | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDefaultPort2::GetServer
helpviewer_keywords: IDebugDefaultPort2::GetServer
ms.assetid: cacb4b74-0f39-471c-af38-54b73f5b2868
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c1d5839db305c1395edc24a95de706cfc2072d8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdefaultport2getserver"></a>IDebugDefaultPort2::GetServer
Esse método obtém uma interface para o servidor que essa porta está em.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetServer(  
   IDebugCoreServer3** ppServer  
);  
```  
  
```csharp  
int GetServer(  
   out IDebugCoreServer3 ppServer  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ppServer`  
 [out] Retorna um objeto que implementa o [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) interface.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md) é implementada pelo Visual Studio e representa o servidor em que a porta está localizada em.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)