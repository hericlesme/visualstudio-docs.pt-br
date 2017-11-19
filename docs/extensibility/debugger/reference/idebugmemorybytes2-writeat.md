---
title: IDebugMemoryBytes2::WriteAt | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cb9b887ff8501516ea063dccf0247b0915de1d63
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Grava o número especificado de bytes de memória, iniciando no endereço especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT WriteAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory  
);  
```  
  
```csharp  
int WriteAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pStartContext`  
 [in] O [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objeto que especifica o local iniciar a gravação de bytes.  
  
 `dwCount`  
 [in] O número de bytes a serem gravados.  
  
 `rgbMemory`  
 [in] Os bytes a serem gravados. Essa matriz deve para ser pelo menos `dwCount` bytes de tamanho.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna `S_FALSE` se nem todos os bytes pode ser gravados ou retorna um código de erro (geralmente `E_FAIL`).  
  
## <a name="remarks"></a>Comentários  
 Se o endereço inicial não está dentro da janela de memória representada por esse [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) do objeto, nenhuma gravação ocorre e um código de erro `E_FAIL` será retornado, mesmo que se sobreponha a quantidade para gravar no espaço de memória.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)