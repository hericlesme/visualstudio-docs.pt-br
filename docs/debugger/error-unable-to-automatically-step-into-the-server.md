---
title: "Erro: Não é possível intervir automaticamente no servidor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.causality_no_server_response
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords: remote debugging, notification error
ms.assetid: 9a370ccc-d358-429c-b285-9b6c0649bc68
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63e8d73b9df650a1d98b0c9f080c7b32cc0a324e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Erro: não é possível intervir automaticamente no servidor
O erro é:  
  
 Não é possível realizar a depuração completa do servidor automaticamente. O depurador não foi notificado antes do procedimento remoto ter sido executado  
  
 Esse erro pode ocorrer quando você está tentando entrar em um serviço da web (consulte [depuração em um serviço XML Web](http://msdn.microsoft.com/en-us/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Pode ocorrer sempre que o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] não estiver configurado corretamente.  
  
 Possíveis causas:  
  
-   O arquivo Web. config para seu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativo não definiu a depuração como "true" no (consulte [modo de depuração em aplicativos ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).  
  
-   Uma versão de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] foi instalado após instalação do Visual Studio. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]deve ser instalado antes do Visual Studio. Para corrigir esse problema, use o Windows **painel de controle > Programas e recursos** para reparar a instalação do Visual Studio.  
  
## <a name="see-also"></a>Consulte também  
 [Erros de depuração remota e solução de problemas](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuração remota](../debugger/remote-debugging.md)