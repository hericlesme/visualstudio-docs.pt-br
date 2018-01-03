---
title: "Erro de processo irrecuperável do Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 02/23/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editor
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-general
ms.workload: multiple
ms.openlocfilehash: 20d3072e1813ff0c94a6479401249681c3481ccd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# Erro de processo irrecuperável do Visual Studio

O Visual Studio 2017 usa vários processos fora do processo para executar tarefas em segundo plano obrigatórias, como testes de unidade em tempo real, analisadores de código e muito mais. Esses processos são executados fora do processo para fornecer vantagens de desempenho do Visual Studio, como permitir que o Visual Studio responda mais rapidamente ao executar trabalhos de longa duração com uso intensivo de recursos. Além disso, como o Visual Studio é um processo de 32 bits, a execução de processos fora do processo fornece ao trabalho com uso intensivo de memória maior espaço de memória no qual operar.

Se um desses processos obrigatórios for encerrado por algum motivo, uma barra de informações pop-up será exibida com a seguinte mensagem:

“Infelizmente, um processo usado pelo Visual Studio encontrou um erro irrecuperável. Recomendamos salvar o trabalho e, em seguida, fechar e reiniciar o Visual Studio.”

Se você receber essa mensagem, deverá salvar o trabalho imediatamente e, em seguida, fechar e reiniciar o Visual Studio. Se não fizer isso, o Visual Studio poderá falhar a qualquer momento.

## Lista de processos

Veja a seguir uma lista de processos fora do processo usados pelo Visual Studio que devem estar em execução para o funcionamento correto do Visual Studio.

- Microsoft.Alm.Shared.Remoting.RemoteContainer.dll
- Microsoft.CodeAnalysis.LiveUnitTesting.EntryPoint
- PerfWatson2.exe
- ServiceHub.Host.Node.x86.exe
- ServiceHub.IdentityHost.exe
- ServiceHub.VSDetouredHost.exe
- ServiceHub.SettingsHost.exe
- ServiceHub.Host.CLR.x86.exe
- ServiceHub.RoslynCodeAnalysisService32.exe
- WindowsAzureGuestAgent.exe
- WindowsAzureTelemetryService.exe
- WaAppAgent.exe
