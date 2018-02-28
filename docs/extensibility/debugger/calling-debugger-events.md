---
title: Chamar o depurador eventos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4a3870921fab82c92b57b9c64dd30bda109c3bcb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="calling-debugger-events"></a>Eventos do depurador de chamada
Os eventos em sessões de depuração ocorrem em uma ordem específica.  
  
## <a name="discussion"></a>Discussão  
 Para entender o padrão de chamadas entre o mecanismo de depuração (DE) e o Gerenciador de sessão de depuração (SDM), a seguir representa a ordem de chamada dos eventos que ocorrem em uma sessão de depuração típica:  
  
1.  [Anexar e desanexar para um programa](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2.  [Iniciando o depurador](../../extensibility/debugger/launching-the-debugger.md)  
  
3.  [Encerrando um programa](../../extensibility/debugger/terminating-a-program.md)  
  
4.  [Criar um ponto de interrupção](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5.  [Quando associado a um ponto de interrupção ou se tornar não associado](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6.  [Erros de ponto de interrupção](../../extensibility/debugger/breakpoint-errors.md)  
  
7.  [Alcançar um ponto de interrupção](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8.  [Excluir um ponto de interrupção](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [Entrar no modo de interrupção](../../extensibility/debugger/entering-break-mode.md)  
  
10. [Entrando no modo de interrupção](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [Avaliação da expressão no modo de interrupção](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [Tratamento de exceções](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## <a name="see-also"></a>Consulte também  
 [Criar um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)