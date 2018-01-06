---
title: 'Como: localizar o nome do processo do ASP.NET | Microsoft Docs'
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
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: aspnet
ms.openlocfilehash: e542e58bab483a1f20029bb66a073ae07d45afba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>Como localizar o nome do processo ASP.NET
Para anexar a um aplicativo do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] em execução, você precisará saber o nome do processo do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]:  

-   Se você estiver executando o ASP.NET Core no IIS ou IISExpress, o nome do processo é dotnet.exe.

-   Se posteriormente você estiver executando o ASP.NET no IIS 6.0, o nome é w3wp.exe.  
  
-   Se você estiver executando o ASP.NET em uma versão anterior do IIS, o nome é aspnet_wp.exe.

-   Se você estiver executando o ASP.NET no IISExpress, o nome é iisexpress.exe.
  
Para aplicativos criados usando versões do Visual Studio antes do Visual Studio 2012, o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] código pode residir no sistema de arquivos e executar no servidor de teste WebDev.WebServer.exe ou WebDev.WebServer40.exe. Nesse caso, você deve anexar WebDev.WebServer.exe ou WebDev.WebServer40.exe em vez do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processo. Essa situação aplica-se somente à depuração local.
  
Aplicativos ASP antigos são executados dentro do processo inetinfo.exe do IIS quando ele está sendo executado no processo.  

### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>Para determinar a versão do IIS no qual o aplicativo está sendo executado  

1.  Verifique se o aplicativo está em execução e, em seguida, no Visual Studio, use o [anexar ao processo](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) comando.

2.  Digite a primeira letra de um nome de processo como w3wp.exe para localizar rapidamente os processos de **processos disponíveis** lista.

    Os processos disponíveis da lista neste tópico indicará quais versões do IIS estão disponíveis, e o processo que está executando o aplicativo.

    > [!NOTE]
    > A partir de 2017 do Visual Studio, você pode usar a caixa de pesquisa para procurar o nome do processo.
  
## <a name="see-also"></a>Consulte também  
 [Anexar a um processo em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)  
 [Pré-requisitos para aplicativos da Web de depuração remota](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Requisitos de sistema](../debugger/aspnet-debugging-system-requirements.md)   
 [Depurar aplicativos ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)