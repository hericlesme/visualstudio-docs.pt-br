---
title: "Erro: O computador remoto não foi possível iniciar comunicações DCOM | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.unmarshal_callback_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8bdd235db0473a956a57d6d6093b5149bac76d3d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Erro: o computador remoto não conseguiu iniciar a comunicação DCOM
Um erro DCOM ocorreu quando o computador remoto tentou se comunicar com o computador local. O computador local é o computador que está  
  
 executando o Visual Studio. Esse erro pode ocorrer por várias razões:  
  
-   O computador local tem um firewall habilitado.  
  
-   A autenticação do Windows do computador remoto para o computador local não está funcionando.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Se o computador local tiver habilitado o Firewall do Windows, consulte [depuração remota](../debugger/remote-debugging.md) para obter instruções sobre como configurar o firewall para depuração local.  
  
2.  Teste a autenticação do Windows tentando abrir um compartilhamento de arquivos no computador local do servidor remoto.  
  
3.  Para restaurar a autenticação do Windows, tente reiniciar os dois computadores. Examine os logs de eventos nos computadores local e remoto para encontrar erros de Kerberos e entre em contato com os administradores de domínio para problemas conhecidos.  
  
## <a name="see-also"></a>Consulte também  
 [Depuração remota](../debugger/remote-debugging.md)