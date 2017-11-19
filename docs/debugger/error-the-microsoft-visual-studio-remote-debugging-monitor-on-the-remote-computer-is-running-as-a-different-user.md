---
title: "Erro: O Monitor de depuração remota do Microsoft Visual Studio no computador remoto está em execução como um usuário diferente | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f3f2c9e0b3f88734d21ae06f1af48409c58766a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Erro: o Monitor de Depuração Remota do Microsoft Visual Studio no computador remoto está sendo executado como um usuário diferente
Ao tentar fazer a depuração remota, você pode receber a seguinte mensagem de erro:  
  
 O Monitor de Depuração Remota do Microsoft Visual Studio no computador está sendo executado como um usuário diferente.  
  
## <a name="cause"></a>Causa  
 Essa mensagem ocorre quando você está depurando no modo Sem Autenticação e o usuário que iniciou o msvsmon não é o usuário que está executando o Visual Studio.  
  
## <a name="solution"></a>Solução  
 A solução melhor e mais segura é executar o Monitor de Depuração Remota (msvsmon.exe) na mesma conta de usuário que o Visual Studio. Se você não pode fazer isso, você pode executar o Monitor de depuração remota em outra conta com o **permitir que qualquer usuário depure** opção selecionada no Monitor de depuração remota **opções** caixa de diálogo.  
  
> [!CAUTION]
>  Conceder permissões a outros usuários para se conectar permite a possibilidade de acidentalmente conectar à sessão de depuração remota incorreta. Depuração no **sem autenticação** modo nunca é seguro e deve ser usado com cuidado.
  
## <a name="see-also"></a>Consulte também  
 [Erros de depuração remota e solução de problemas](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuração remota](../debugger/remote-debugging.md)