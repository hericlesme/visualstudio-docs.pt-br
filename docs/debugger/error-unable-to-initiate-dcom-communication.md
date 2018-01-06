---
title: "Erro: Não é possível iniciar a comunicação DCOM | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.unmarshal_server_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4aead8cd4396df540779fdeebec953859122fd47
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Erro: não é possível iniciar a comunicação DCOM
Um erro DCOM ocorreu quando o computador local tentou se comunicar com o computador remoto. Isso é causado por um firewall no servidor remoto ou por autenticação do Windows quebrada no computador remoto.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se o computador remoto tiver habilitado o Firewall do Windows, consulte [depuração remota](../debugger/remote-debugging.md) para obter instruções sobre como configurar o firewall para depuração local.  
  
-   Para restaurar a autenticação do Windows, tente reiniciar os dois computadores. Examine os logs de eventos nos computadores local e remoto para encontrar erros de Kerberos e entre em contato com os administradores de domínio para problemas conhecidos.  
  
## <a name="see-also"></a>Consulte também  
 [Depuração remota](../debugger/remote-debugging.md)