---
title: 'Erro: O Monitor de depuração remota do Microsoft Visual Studio no computador remoto está sendo executado como um usuário diferente | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- -anyuser option
- anyuser option
- Remote Debugging Monitor
- remote debugging, Remote Debugging Monitor
- msvsmon.exe
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5256feb22e09eb75fa8f4d5a50e8beafeec8f97d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47466728"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user"></a>Erro: o Monitor de Depuração Remota do Microsoft Visual Studio no computador remoto está sendo executado como um usuário diferente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [erro: O Microsoft Visual Studio Monitor de depuração remota no computador remoto está em execução como um usuário diferente](https://docs.microsoft.com/visualstudio/debugger/error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user).  
  
Ao tentar fazer a depuração remota, você pode receber a seguinte mensagem de erro:  
  
 O Monitor de Depuração Remota do Microsoft Visual Studio no computador está sendo executado como um usuário diferente.  
  
## <a name="cause"></a>Causa  
 Essa mensagem ocorre quando você está depurando no modo Sem Autenticação e o usuário que iniciou o msvsmon não é o usuário que está executando o Visual Studio.  
  
## <a name="solution"></a>Solução  
 A solução melhor e mais segura é executar o Monitor de Depuração Remota (msvsmon.exe) na mesma conta de usuário que o Visual Studio. Se você não pode fazer isso, você pode executar o Monitor de depuração remota em outra conta com o **permitir que qualquer usuário depure** opção selecionada no Monitor de depuração remota **opções** caixa de diálogo.  
  
> [!CAUTION]
>  Conceder permissões a outros usuários para se conectar permite a possibilidade de acidentalmente conectar à sessão de depuração remota incorreta. Depuração no **sem autenticação** modo nunca é seguro e deve ser usado com cuidado.  
  
 Para obter mais informações, consulte [iniciar o Monitor de depuração remota](http://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c).  
  
## <a name="see-also"></a>Consulte também  
 [Solução de problemas e erros de depuração remota](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuração remota](../debugger/remote-debugging.md)



