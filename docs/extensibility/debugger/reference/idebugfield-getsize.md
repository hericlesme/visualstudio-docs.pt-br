---
title: IDebugField::GetSize | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b6c06a9fd218029c59f2ee004d5c421363530af1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugfieldgetsize"></a>IDebugField::GetSize
Esse método obtém o tamanho de um campo, em bytes.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetSize(   
   DWORD* pdwSize  
);  
```  
  
```csharp  
int GetSize(  
   out uint pdwSize  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pdwSize`  
 [out] Retorna o tamanho.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Todos os campos têm um tipo e todos os tipos têm um tamanho. Por exemplo, um campo com um tipo de bytes tem um tamanho de 1 byte.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)