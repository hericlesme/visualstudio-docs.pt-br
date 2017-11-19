---
title: IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
helpviewer_keywords: IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
ms.assetid: 07b20866-e598-4783-9ecc-6aa8625c8804
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 438a773ce80d7196644e3e907a1a2b26685bfc44
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebuginterceptexceptioncompleteevent2getinterceptcookie"></a>IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie
Chamado quando o processamento de uma exceção interceptada foi concluída.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetInterceptCookie(  
   UINT64* pqwCookie  
);  
```  
  
```csharp  
int GetInterceptCookie(  
   out ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pqwCookie`  
 [out] Valor exclusivo que é associado à exceção que foi interceptada.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna o código de erro.  
  
## <a name="remarks"></a>Comentários  
 Após o [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) método concluiu o processamento de uma exceção interceptada, ele envia o [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) eventos. O manipulador pode usar o `GetInterceptCookie` método para recuperar o valor exclusivo associado com a exceção (o mesmo valor passado para o `InterceptCurrentException` método).  
  
## <a name="see-also"></a>Consulte também  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)