---
title: IDebugThread2::SetNextStatement | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 55482e4bf3b4795f7c7f036c0074e456fd642a33
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47475726"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugThread2::SetNextStatement](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugthread2-setnextstatement).  
  
Define o ponteiro de instrução atual para o contexto de código fornecida.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
 [in] Uma [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que descreve o local do código prestes a ser executada e seu contexto.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. A tabela a seguir mostra os outros valores possíveis.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|A próxima instrução não pode ser em um quadro de pilha mais profundo na pilha do quadro.|  
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|A próxima instrução não está associada com qualquer quadro na pilha.|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Alguns mecanismos de depuração não é possível definir a próxima instrução após uma exceção.|  
  
## <a name="remarks"></a>Comentários  
 O ponteiro de instrução indica a próxima instrução ou instrução para executar. Esse método é usado para tentar novamente uma linha de código-fonte ou para forçar a execução continue em outra função, por exemplo.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)

