---
title: Ocorreu um erro de DCOM durante a tentativa de contatar o computador remoto. O acesso foi negado. | Microsoft Docs
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
- vs.debug.remote.dcom_access_denied
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cabac4997480b626714c129daef0511643ae2a50
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47473691"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Ocorreu um erro de DCOM durante a tentativa de contatar o computador remoto. O acesso foi negado.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A versão mais recente deste tópico pode ser encontrada em [erro DCOM um ocorreu ao tentar contatar o computador remoto. O acesso é negado. ](https://docs.microsoft.com/visualstudio/debugger/a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied).  
  
Depuração remota usa DCOM para se comunicar entre os computadores locais e remotos nas seguintes situações:  
  
-   O depurador está definido como **modo de compatibilidade nativa** ou **modo de compatibilidade gerenciado** check-in a **Ferramentas / opções / depuração** página  
  
-   Você está depurando C++ gerenciado (C + + / CLI) código.  
  
-   No Visual Studio 2013, quando **habilitar nativo editar e continuar** check-in a **Ferramentas / opções / depuração** página  
  
-   Alguns cenários de depuração de terceiros  
  
 Esse erro ocorre quando o processo do Visual Studio não puder se autenticar (ou as credenciais fornecidas forem julgadas insuficientes) para o processo remoto do depurador sobre DCOM. Uma ou mais das seguintes alternativas podem resolver o problema:  
  
-   Desative **modo de compatibilidade nativa** e **modo de compatibilidade gerenciado**.  
  
-   No Visual Studio 2013, desative **habilitar nativo editar e continuar**.  
  
-   Reinicializar ambos os computadores.  
  
-   Se a depuração remota exigir a inserção de credenciais, verifique a opção para salvar as credenciais.  
  
## <a name="see-also"></a>Consulte também  
 [Solução de problemas e erros de depuração remota](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuração remota](../debugger/remote-debugging.md)



