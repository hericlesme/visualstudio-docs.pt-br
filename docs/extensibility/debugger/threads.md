---
title: Threads | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a2754d3b1b15771f876855e7ca7d1dc510748308
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31125780"
---
# <a name="threads"></a>Threads
Em termos de arquitetura do depurador, um **thread**:  
  
-   É a unidade fundamental de computação. Um thread sequencialmente executa as instruções dentro do contexto de uma pilha de chamadas, movendo de contexto de um código para o próximo.  
  
-   Pode identificar a mesmo e o programa está em execução e pode ser chamado, suspenso e retomado. Um thread também pode enumerar seus quadros de pilha associado e, em algumas condições, pode ser movido para outro quadro de pilha. Considerando o contexto de um quadro de pilha, um thread pode retornar o thread lógico associado, se houver. Um thread tem propriedades, como uma contagem de suspender, que podem ser exibidos na janela de Threads do IDE.  
  
-   É representado por um [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interface, normalmente criado por um mecanismo de depuração (DE) ou a máquina virtual como consequência de executar um programa.  
  
## <a name="see-also"></a>Consulte também  
 [Programas](../../extensibility/debugger/programs.md)   
 [Quadros de pilhas](../../extensibility/debugger/stack-frames.md)   
 [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Gerenciador de sessão de depuração](../../extensibility/debugger/session-debug-manager.md)