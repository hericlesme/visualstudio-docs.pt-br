---
title: "Erro: RPC requer autenticação | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 73cd474d415a49b6dd9075559d8618289b1b0d21
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="error-rpc-requires-authentication"></a>Erro: RPC requer autenticação
O depurador do Visual Studio não pode se conectar ao computador remoto. Uma política RPC está habilitada no computador local, impedindo a depuração remota.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Executar `\` *windir*`\system32\regedt32.exe`  
  
2.  Localize e exclua `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Reinicie o computador para que a alteração do Registro entre em vigor.  
  
4.  Se o problema persistir, entre em contato com seu administrador de domínio sobre o **configuração do computador > modelos administrativos > sistema > chamada de procedimento remoto > restrições para os clientes não autenticados RPC** política de grupo configuração.