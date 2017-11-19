---
title: "Erro: Verifique se o DNS está configurado corretamente no computador de destino | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.callback_dns_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 2d364caf-73af-4186-bf9b-af186331cbe8
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6711ae54c87e5e71a643fee3c019c8214294c09a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Erro: verifique se o DNS está configurado corretamente no computador de destino
Ao tentar fazer a depuração remota, você pode receber a seguinte mensagem de erro:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Esse erro ocorre quando o computador de destino não pode resolver o nome do computador host do depurador do Visual Studio. Verifique as configurações DNS no computador de destino.  
  
-   Para obter informações sobre como exibir a configuração de DNS no Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 ou Windows Server 2008 R2, fazer isso: no **iniciar** menu, escolha **ajuda e suporte** e, em seguida, procure **configurações TCP/IP de alteração**.  
  
-   Para obter mais informações, vá para [site do Microsoft Windows](http://go.microsoft.com/fwlink/?LinkId=252720) e procure **configurações TCP/IP de alteração**.  
  
 Se você não conseguir resolver o problema de DNS, tente executar o Depurador Remoto em uma conta diferente. Esse erro ocorre somente quando você está executando o Depurador Remoto sob a conta Serviço de Rede ou Sistema Local. Se você executar o Depurador Remoto em outra conta, ele poderá usar a autenticação NTLM, que não exige DNS. . Para o procedimento, consulte [erro: serviço de depurador remoto a do Visual Studio no computador de destino não pode se conectar novamente a esse computador](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).