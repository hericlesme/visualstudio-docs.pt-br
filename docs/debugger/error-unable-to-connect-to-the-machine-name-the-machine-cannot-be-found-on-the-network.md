---
title: "Erro: Não é possível conectar à máquina &lt;nome&gt;. A máquina não pode ser encontrada na rede. | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e8b7ef99717f0a68fbd17245958840c89cdf8544
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Erro: Não é possível conectar à máquina &lt;nome&gt;. A máquina não pode ser encontrada na rede.
Esse comportamento ocorre se uma das seguintes condições for verdadeira:  
  
-   Sua conexão com o computador remoto foi interrompida.  
  
-   Sua conta de usuário no computador remoto está desabilitada.  
  
-   Sua senha no computador remoto expirou.  
  
### <a name="to-resolve-this-behavior"></a>Para resolver esse comportamento:  
  
-   Verifique se o computador local e o computador remoto estão na mesma rede. Para fazer isso, use o Microsoft Windows Explorer (ou Pesquisador de Arquivos) para tentar acessar o computador remoto.  
  
     — e —  
  
-   Verifique se a conta de usuário que você está usando para se conectar ao computador remoto está habilitada.  
  
     — e —  
  
-   Verifique se a senha que você está usando para se conectar ao computador remoto está válida e não expirou.  
  
## <a name="see-also"></a>Consulte também  
 [Depuração remota](../debugger/remote-debugging.md)   
 [Preparação e configurações do depurador](../debugger/debugger-settings-and-preparation.md)