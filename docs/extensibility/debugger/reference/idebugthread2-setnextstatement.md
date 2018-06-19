---
title: IDebugThread2::SetNextStatement | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e59d4087e44458ecd49efd5d7be9f45e68c6da2b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31119527"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
Define o ponteiro de instrução atual para o contexto de código fornecido.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```csharp  
int SetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pStackFrame`  
 Reservado para uso futuro; definido como um valor nulo.  
  
 `pCodeContext`  
 [in] Um [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que descreve o local do código prestes a ser executada e o contexto.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro. A tabela a seguir mostra os outros valores possíveis.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|A próxima instrução não pode estar em um quadro de pilha mais profundo na pilha de quadro.|  
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|A próxima instrução não está associada com qualquer quadro na pilha.|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Alguns mecanismos de depuração não é possível definir a próxima instrução após uma exceção.|  
  
## <a name="remarks"></a>Comentários  
 O ponteiro de instrução indica a próxima instrução ou instrução execute. Esse método é usado para repetir uma linha do código-fonte ou para forçar a execução continue em outra função, por exemplo.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)