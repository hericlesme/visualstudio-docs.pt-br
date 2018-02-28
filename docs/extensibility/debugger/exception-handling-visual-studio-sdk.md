---
title: "Exceção tratamento (SDK do Visual Studio) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 88a862c26dad97eecdb5f372f41a76d7886f32be
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="exception-handling-visual-studio-sdk"></a>Exceção tratamento (SDK do Visual Studio)
O exemplo a seguir descreve o processo que ocorre quando as exceções são geradas.  
  
## <a name="exception-handling-process"></a>Processo de tratamento de exceção  
  
1.  Quando uma exceção é lançada pela primeira vez, mas antes que ela é tratada pelo manipulador de exceção no programa que está sendo depurado, o mecanismo de depuração (DE) envia um [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) para o Gerenciador de depuração de sessão (SDM) como um evento de parada. O `IDebugExceptionEvent2` é enviado se apenas as configurações para a exceção (especificada na caixa de diálogo exceções no pacote de depuração) especificam que o usuário deseja parar em notificações de exceção de primeira chance.  
  
2.  As chamadas SDM [IDebugExceptionEvent2::GetException](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) para obter a propriedade de exceção.  
  
3.  As chamadas de pacote de depuração [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) para determinar as opções para apresentar ao usuário.  
  
4.  O pacote de depuração pede ao usuário como lidar com a exceção abrindo uma caixa de diálogo de exceção de primeira chance.  
  
5.  Se o usuário optar por continuar, o SDM chama [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).  
  
    -   Se o método retorna S_OK, chamadas [IDebugExceptionEvent2::PassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).  
  
         -ou-  
  
         Se o método retornar S_FALSE, o programa que está sendo depurado receberá a segunda oportunidade de lidar com a exceção.  
  
6.  Se o programa que está sendo depurado não tem um manipulador para uma exceção de segunda chance, envia o DE um `IDebugExceptionEvent2` para SDM como **EVENT_SYNC_STOP**.  
  
7.  O pacote de depuração pede ao usuário como lidar com a exceção abrindo uma caixa de diálogo de exceção de primeira chance.  
  
8.  As chamadas de pacote de depuração [IDebugExceptionEvent2::CanPassToDebuggee](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) para determinar as opções para apresentar ao usuário.  
  
9. O pacote de depuração pede ao usuário como lidar com a exceção abrindo uma caixa de diálogo de exceção de segunda chance.  
  
10. Se o método retorna S_OK, chamadas `IDebugExceptionEvent2::PassToDebuggee`.  
  
## <a name="see-also"></a>Consulte também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)