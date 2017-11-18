---
title: "Erro: Não é possível iniciar a comunicação DCOM | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.unmarshal_server_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 2a7b27e6-2526-4f32-bc4d-eaee447f24ec
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c80f2455b53cba46f0f2f753c55ff1b7e9dad8d6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Erro: não é possível iniciar a comunicação DCOM
Um erro DCOM ocorreu quando o computador local tentou se comunicar com o computador remoto. Isso é causado por um firewall no servidor remoto ou por autenticação do Windows quebrada no computador remoto.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se o computador remoto tiver habilitado o Firewall do Windows, consulte [depuração remota](../debugger/remote-debugging.md) para obter instruções sobre como configurar o firewall para depuração local.  
  
-   Para restaurar a autenticação do Windows, tente reiniciar os dois computadores. Examine os logs de eventos nos computadores local e remoto para encontrar erros de Kerberos e entre em contato com os administradores de domínio para problemas conhecidos.  
  
## <a name="see-also"></a>Consulte também  
 [Depuração remota](../debugger/remote-debugging.md)