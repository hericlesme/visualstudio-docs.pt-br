---
title: 'Erro: O Monitor de depuração remota do Microsoft Visual Studio no computador remoto não tem permissão para se conectar a este computador | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.error.access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, Windows version error
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 266a301bca4953066621d759518c1754052dfeb2
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/11/2018
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Erro: o Monitor de Depuração Remota do Microsoft Visual Studio no computador remoto não tem permissão para se conectar a este computador
Esse erro ocorre quando o usuário que está tentando executar o Monitor de Depuração Remota do Visual Studio (msvsmon) não tem uma conta no computador local.  
  
### <a name="to-fix-this-problem"></a>Para corrigir esse problema  
  
-   Adicione uma conta de usuário ao computador host do depurador do Visual Studio, com o mesmo nome e senha que a conta usuário que está executando msvsmon no computador remoto,  
  
     \- ou -  
  
-   Execute msvsmon como um usuário que tem permissão para chamar no computador local. Isso significa que o usuário deve ser usuário de domínio e administrador no computador de msvsmon. Você pode especificar a conta de usuário para executar msvsmon de uma de duas maneiras:  
  
    -   Clique no ícone msvsmon e escolha **executar como** no menu de atalho  
  
     \- ou -  
  
    -   No prompt de comando, execute `runas.exe`.  
  
## <a name="see-also"></a>Consulte também  
 [Erros de depuração remota e solução de problemas](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuração remota](../debugger/remote-debugging.md)