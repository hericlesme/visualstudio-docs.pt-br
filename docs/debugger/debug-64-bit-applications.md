---
title: Depurar aplicativos de 64 bits | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], 64-bit
- 64-bit debugging
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
caps.latest.revision: "32"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5c3840cc7d43c3e30dda0317674ffb8cd664a262
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="debug-64-bit-applications"></a>Depurar aplicativos de 64 bits
Você pode depurar um aplicativo de 64 bits que está sendo executado no computador local ou em um computador remoto.  
  
 Para depurar um aplicativo de 64 bits em execução em um computador remoto, consulte [depuração remota](../debugger/remote-debugging.md).  
  
 Para depurar aplicativos de 64 bits localmente, o Visual Studio usa um processo de trabalho de 64 bits (msvsmon.exe) para executar as operações de baixo nível que não podem ser feitas dentro de processo do Visual Studio de 32 bits.  
  
 Não há suporte para a depuração de modo misto para processos de 64 bits que usam o .NET Framework versão 3.5 ou anterior.  
  
## <a name="debug-a-64-bit-application"></a>Depurar um aplicativo de 64 bits  
 Para tentar depurar um aplicativo de 64 bits:  
  
1.  Crie uma solução do Visual Studio, por exemplo um console aplicativo c#.  
  
2.  Defina a configuração de 64 bits usando o Configuration Manager. Para obter mais informações, consulte [como: configurar projetos para destinar plataformas](../ide/how-to-configure-projects-to-target-platforms.md).  
  
3.  Neste ponto, a versão de 64 bits do depurador remoto (msvsmon.exe) inicia. Ele é executado, desde que a solução com a configuração de 64 bits é aberta.  
  
4.  Inicie a depuração. Você deve ter a mesma experiência assim como acontece com uma configuração de 32 bits. Se você obtiver erros, consulte a seção de solução de problemas abaixo.  
  
## <a name="troubleshooting-64-bit-debugging"></a>Solucionando problemas de depuração de 64 bits  
 Você pode ver um erro: "uma operação de depuração de 64 bits está demorando mais do que o esperado." Nesse caso, o Visual Studio enviou uma solicitação para a versão de 64 bits do msvsmon.exe e levou muito tempo para o resultado da solicitação a ser retornado.  
  
 Há duas causas principais para este erro:  
  
-   Você tem o software de segurança de rede instalado no computador que fez a pilha de rede não é confiável e ele descartado pacotes ultrapassou o localhost. Tente desabilitar todos os softwares de segurança de rede e veja se isso resolve. Nesse caso, de relatório para o fornecedor do software de segurança de rede que o software é interferir com o tráfego de host local.  
  
-   Você está executando em um problema de suspensão ou de desempenho com o Visual Studio. Se o problema ocorrer regularmente, você pode coletar despejos do Visual Studio (devenv.exe) e o processo de trabalho (msvsmon.exe) e enviá-los à Microsoft. Para obter informações sobre um problema de emissão de relatórios, consulte [como relatar um problema com o Visual Studio](../ide/How-to-Report-a-Problem-with-Visual-Studio-2017.md).
  
## <a name="see-also"></a>Consulte também  
 [Aplicativos de 64 bits](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Configurando programas para 64 bits](/cpp/build/configuring-programs-for-64-bit-visual-cpp)   
 [Suporte de 64 bits do Visual Studio IDE](../ide/visual-studio-ide-64-bit-support.md)   
 [Usando arquivos de despejo](../debugger/using-dump-files.md)   
 [Depuração remota](../debugger/remote-debugging.md)