---
title: Programa de controle | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8c227f38c926cb6d764ddf47541b8bd744eb6f7c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="program-control"></a>Controle do programa
No Visual Studio de depuração, todos os procedimentos passo a passo e continuar rotinas ocorrerem no nível do programa:  
  
-   Ou seja, definir a próxima instrução, a configuração de seu computador para a próxima instrução a ser executada em um ambiente de quadro específico  
  
-   Ou seja, executar, continue sair do modo de depuração  
  
-   Passo a passo para a próxima instrução  
  
-   Continuando com o modo de depuração atual  
  
-   Suspendendo threads contidos pelo programa  
  
-   Retomando threads contidos pelo programa  
  
> [!NOTE]
>  Exibindo a pilha de chamadas é implementado em nível de thread. Para enumerar as informações do quadro ao exibir a pilha de chamadas para um thread, você deve implementar todos os métodos do [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) interface.  
  
## <a name="methods-of-program-control"></a>Métodos de controle do programa  
 A tabela a seguir mostra os métodos de [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) que deve ser implementado para um mecanismo de depuração minimamente funcional (DE) e controle de execução.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Continua a execução de todos os segmentos contidos por um programa de um estado parado. Necessário para o controle de execução.|  
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Continua a execução de todos os segmentos contidos por um programa de um estado parado. Necessário para o controle de execução.|  
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Executa uma etapa em determinado thread. Continuar em execução por todos os outros segmentos contidos pelo programa. Necessário para o controle de execução.|  
  
 Para programas multithread, você também deve implementar o [IDebugProgram2::EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) método e todos os métodos do [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) interface.  
  
## <a name="see-also"></a>Consulte também  
 [Controle de execução e avaliação de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)