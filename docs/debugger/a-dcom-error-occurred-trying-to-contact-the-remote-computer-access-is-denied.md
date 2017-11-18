---
title: Erro de DCOM ao tentar contatar o computador remoto. O acesso foi negado. | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.remote.dcom_access_denied
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: "27"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe153a5252603cf967b396932a6479a8df437a08
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Erro de DCOM ao tentar contatar o computador remoto. O acesso foi negado.
Depuração remota usa DCOM para se comunicar entre os computadores locais e remotos nas seguintes situações:  
  
-   O depurador está definido como **modo de compatibilidade nativo** ou **modo de compatibilidade gerenciado** check-in a **Ferramentas > Opções > depuração** página  
  
-   Você está depurando C++ gerenciado (C + + CLI) código.  
  
-   No Visual Studio 2013, quando **habilitar nativo editar e continuar** check-in a **Ferramentas > Opções > depuração** página  
  
-   Alguns cenários de depuração de terceiros  
  
 Esse erro ocorre quando o processo do Visual Studio não puder se autenticar (ou as credenciais fornecidas forem julgadas insuficientes) para o processo remoto do depurador sobre DCOM. Uma ou mais das seguintes alternativas podem resolver o problema:  
  
-   Desativar **modo de compatibilidade nativo** e **modo de compatibilidade gerenciado**.  
  
-   No Visual Studio 2013, desative **habilitar nativo editar e continuar**.  
  
-   Reinicializar ambos os computadores.  
  
-   Se a depuração remota exigir a inserção de credenciais, verifique a opção para salvar as credenciais.  
  
## <a name="see-also"></a>Consulte também  
 [Erros de depuração remota e solução de problemas](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuração remota](../debugger/remote-debugging.md)