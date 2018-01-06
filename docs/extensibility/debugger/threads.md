---
title: Threads | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f611284584b091fca390f660b3e840f6cebe048c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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