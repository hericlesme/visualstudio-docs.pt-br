---
title: IDebugDisassemblyStream2::GetCodeLocationId | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b042a3a88ed1e64bf7093c0e1ce52da746186921
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
Retorna um identificador de local de código para um contexto de código específico.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCodeLocationId(   
   IDebugCodeContext2* pCodeContext,  
   UINT64*             puCodeLocationId  
);  
```  
  
```csharp  
int GetCodeLocationId(   
   IDebugCodeContext2 pCodeContext,  
   out ulong          puCodeLocationId  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pCodeContext`  
 [in] Um [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto a ser convertido em um identificador.  
  
 `puCodeLocationId`  
 [out] Retorna o identificador de local de código. Consulte Observações.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro. Retorna `E_CODE_CONTEXT_OUT_OF_SCOPE` se o contexto de código é válido, mas fora do escopo.  
  
## <a name="remarks"></a>Comentários  
 O identificador de local de código é específico para o mecanismo de depuração (DE) com suporte a desmontagem. Esse identificador de local é usado internamente pelo DE rastrear posições no código e normalmente é um endereço ou o deslocamento de algum tipo. O único requisito é que, se o contexto do código de um local for menor que o contexto do código de outro local, em seguida, o identificador de local de código correspondente o primeira de contexto de código também deve ser menor que o identificador de local de código do contexto de código do segundo.  
  
 Para recuperar o contexto do código de um identificador de local de código, chame o [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)