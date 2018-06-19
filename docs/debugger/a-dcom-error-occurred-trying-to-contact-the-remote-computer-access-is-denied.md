---
title: Erro de DCOM ao tentar contatar o computador remoto. O acesso foi negado. | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.remote.dcom_access_denied
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8533201bfd052b2131ba302e8e1c451f62e5b50a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31466400"
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