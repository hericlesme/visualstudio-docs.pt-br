---
title: Depurar pacote | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a2cbb124dcb2d2d7a0bbcba1bc57eb3c704dd770
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="debug-package"></a>Depurar pacote
O pacote de depuração é executado no shell do Visual Studio e gerencia todos da interface do usuário. Ele consome o interfaces de depuração do Visual Studio e se comunica com o Gerenciador de sessão de depuração (SDM).  
  
 Eventos de interrupção enviados por meio do SDM alternar o depurador do modo de execução para o modo de interrupção e mudar o foco para o programa onde a quebra ocorreu. O pacote de depuração rastreia o quadro de pilhas e o encadeamento das informações enviadas a ele pelos eventos.  
  
 O pacote de depuração não tem idioma ou dependências de tempo de execução. Não é necessário implementar ou modificar o pacote de depuração.  
  
 O pacote de depuração é implementado por vsdebug.dll.  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciador de sessão de depuração](../../extensibility/debugger/session-debug-manager.md)   
 [Quadros de pilhas](../../extensibility/debugger/stack-frames.md)   
 [Threads](../../extensibility/debugger/threads.md)   
 [Componentes do depurador](../../extensibility/debugger/debugger-components.md)