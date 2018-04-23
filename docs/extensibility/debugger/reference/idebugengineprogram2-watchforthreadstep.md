---
title: IDebugEngineProgram2::WatchForThreadStep | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f7c897c4c5b8488766f72723f3e85909281abbf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Aguarda a execução (ou para assistir a execução) para ocorrer em determinado thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT WatchForThreadStep(   
   IDebugProgram2* pOriginatingProgram,  
   DWORD           dwTid,  
   BOOL            fWatch,  
   DWORD           dwFrame  
);  
```  
  
```csharp  
int WatchForThreadStep(   
   IDebugProgram2 pOriginatingProgram,  
   uint           dwTid,  
   int            fWatch,  
   uint           dwFrame  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pOriginatingProgram`  
 [in] Um [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa o programa que está sendo passado.  
  
 `dwTid`  
 [in] Especifica o identificador do segmento para assistir.  
  
 `fWatch`  
 [in] Diferente de zero (`TRUE`) significa começar a observar para execução no thread identificado por `dwTid`; caso contrário, zero (`FALSE`) significa parar de monitorar para execução em `dwTid`.  
  
 `dwFrame`  
 [in] Especifica um índice de quadro que controla o tipo de etapa. Quando isso é valor é zero (0), o tipo de etapa é "entrar" e o programa deve ser interrompida sempre que o thread identificada pelo `dwTid` executa. Quando `dwFrame` é diferente de zero, o tipo de etapa é "contornar" e o programa deve parar apenas se o thread identificado por `dwTid` está em execução em um quadro cujo índice é igual ou superior na pilha que `dwFrame`.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Quando o Gerenciador de sessão de depuração (SDM) etapas de um programa, identificado pelo `pOriginatingProgram` parâmetro, ele notifica todos os outros programas conectados por chamar esse método.  
  
 Esse método é aplicável somente a revisão do mesmo thread.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)