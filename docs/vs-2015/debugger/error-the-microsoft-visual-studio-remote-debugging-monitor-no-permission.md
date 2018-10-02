---
title: 'Erro: O Monitor de depuração remota do Microsoft Visual Studio no computador remoto não tem permissão para se conectar a este computador | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.access_denied_oncallback
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
- remote debugging, Windows version error
ms.assetid: ba08a59b-6dbc-4bbc-9c52-379d3bf5241f
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a62f20afc5ba57da64205491a3c5dfeabd75daf
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/29/2018
ms.locfileid: "47587379"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer"></a>Erro: o Monitor de Depuração Remota do Microsoft Visual Studio no computador remoto não tem permissão para se conectar a este computador
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [erro: O Microsoft Visual Studio Monitor de depuração remota no computador remoto não tem permissão para se conectar a este computador](https://docs.microsoft.com/visualstudio/debugger/error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-does-not-have-permission-to-connect-to-this-computer).  
  
Esse erro ocorre quando o usuário que está tentando executar o Monitor de Depuração Remota do Visual Studio (msvsmon) não tem uma conta no computador local.  
  
### <a name="to-fix-this-problem"></a>Para corrigir esse problema  
  
-   Adicione uma conta de usuário ao computador host do depurador do Visual Studio, com o mesmo nome e senha que a conta usuário que está executando msvsmon no computador remoto,  
  
     \- ou -  
  
-   Execute msvsmon como um usuário que tem permissão para chamar no computador local. Isso significa que o usuário deve ser usuário de domínio e administrador no computador de msvsmon. Você pode especificar a conta de usuário para executar msvsmon de uma de duas maneiras:  
  
    -   Clique com botão direito no ícone de msvsmon e escolha **executar como** no menu de atalho  
  
     \- ou -  
  
    -   No prompt de comando, execute `runas.exe`.  
  
## <a name="see-also"></a>Consulte também  
 [Depuração remota entre domínios](http://msdn.microsoft.com/library/8e697ce1-55e8-4ab0-a05f-f87225e2f29b)   
 [Solução de problemas e erros de depuração remota](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuração remota](../debugger/remote-debugging.md)



