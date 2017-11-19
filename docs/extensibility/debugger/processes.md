---
title: Processos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f295dd93580caee4b6288febf7e83c09736b6080
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="processes"></a>Processos
Em termos de arquitetura do depurador, um **processo**:  
  
-   É um contêiner para um conjunto de programas. É estreitamente análogo a um processo do Windows, que é um contêiner para um conjunto de threads.  
  
-   Pode identificar-se por nome, identificador ou identificador físico.  
  
-   Pode enumerar todos os programas em execução (e seus threads).  
  
-   Descreve em si, a porta que ele está sendo executado no e no computador que contém.  
  
-   Pode criar um ou mais programas, encerrar qualquer um dos programas que cria ou fazer com que um programa para parar.  
  
-   É representado por um [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) interface, que é criado quando o processo é iniciado. Um processo é iniciado ou o depuração Gerenciador de sessão (SDM) ou [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 O pacote de depuração pode anexar um mecanismo de depuração (DE) para um processo chamando [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Isso significa que o DE anexa a todos os possíveis programas em execução no processo que pode manipular. Por exemplo, se o common language runtime DE anexar a um processo, ele anexa apenas para programas que estão executando o código gerenciado.  
  
## <a name="see-also"></a>Consulte também  
 [Programas](../../extensibility/debugger/programs.md)   
 [Threads](../../extensibility/debugger/threads.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Depurar pacote](../../extensibility/debugger/debug-package.md)   
 [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Anexar](../../extensibility/debugger/reference/idebugprocess2-attach.md)