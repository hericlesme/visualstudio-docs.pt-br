---
title: IDebugDisassemblyStream2::GetCodeContext | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDisassemblyStream2::GetCodeContext
helpviewer_keywords: IDebugDisassemblyStream2::GetCodeContext
ms.assetid: a6d0ae82-7617-4915-9713-369abe3e2e53
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1c40a76ffeae198a9d4a5a41b438262a342d877e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdisassemblystream2getcodecontext"></a>IDebugDisassemblyStream2::GetCodeContext
Retorna um objeto de contexto de código correspondente a um identificador de local de código especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCodeContext(   
   UINT64               uCodeLocationId,  
   IDebugCodeContext2** ppCodeContext  
);  
```  
  
```csharp  
int GetCodeContext(   
   ulong                  uCodeLocationId,  
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `uCodeLocationId`  
 [in] Especifica o identificador de local de código. Consulte a seção comentários para o [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) método para obter uma descrição de um identificador de local de código.  
  
 `ppCodeContext`  
 [out] Retorna um [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que representa o contexto de código associado.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 O identificador de local de código pode ser retornado de uma chamada para o [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md) método e podem aparecer o [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estrutura.  
  
 Para converter um contexto de código em um identificador de local de código, chame o [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)   
 [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)