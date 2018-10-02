---
title: IDebugThread2::CanSetNextStatement | Microsoft Docs
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
- IDebugThread2::CanSetNextStatement
helpviewer_keywords:
- IDebugThread2::CanSetNextStatement
ms.assetid: 7014af80-ff4f-4790-a34b-0528918d1fa3
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 40cf5eba5cfb5a7e960ed8905141d4058d926d39
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47474632"
---
# <a name="idebugthread2cansetnextstatement"></a>IDebugThread2::CanSetNextStatement
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [IDebugThread2::CanSetNextStatement](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugthread2-cansetnextstatement).  
  
Determina se o ponteiro de instrução atual pode ser definido para o registro de ativação.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT CanSetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```csharp  
int CanSetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pStackFrame`  
 Reservado para uso futuro; definido como um valor nulo. Se esse for um valor nulo, use o quadro de pilhas atual.  
  
 `pCodeContext`  
 [in] Uma [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que descreve o local do código prestes a ser executada e seu contexto.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Se esse método retornar `S_OK`, em seguida, chamar o [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md) método, na verdade, definir a próxima instrução.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)

