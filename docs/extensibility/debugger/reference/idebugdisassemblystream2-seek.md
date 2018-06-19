---
title: IDebugDisassemblyStream2::Seek | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 55a8c2c205627130e8dd6dd28f288b2d3dee9d2e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103585"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Move o ponteiro de leitura no fluxo de desmontagem um determinado número de instruções em relação a uma posição especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```csharp  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwSeekStart`  
 [in] Um valor da [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) enumeração que especifica a posição relativa para iniciar o processo de busca.  
  
 `pCodeContext`  
 [in] O [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que representa o contexto de código que a operação de busca é relativo. Esse parâmetro é usado somente se `dwSeekStart`  =  `SEEK_START_CODECONTEXT`; caso contrário, esse parâmetro é ignorado e pode ser um valor nulo.  
  
 `uCodeLocationId`  
 [in] O identificador de local de código que a operação de busca é relativo. Esse parâmetro é usado se `dwSeekStart`  =  `SEEK_START_CODELOCID`; caso contrário, esse parâmetro é ignorado e pode ser definido como 0. Consulte a seção comentários para o [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) método para obter uma descrição de um identificador de local de código.  
  
 `iInstructions`  
 [in] O número de instruções para mover em relação à posição especificada na `dwSeekStart`. Esse valor pode ser negativo para mover com versões anteriores.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se a posição de busca de um ponto além da lista de instruções disponíveis. Caso contrário, retornará um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Se a busca de uma posição antes do início da lista, a posição de leitura é definida como a primeira instrução na lista. Se o consulte era uma posição após o final da lista, a posição de leitura será definida para a última instrução na lista.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)