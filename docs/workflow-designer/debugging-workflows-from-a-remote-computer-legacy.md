---
title: Designer de fluxo de trabalho - depuração de fluxos de trabalho de um computador remoto (legados)
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 391180cd76fe5e0cccca802ba1cbfb78277dabc1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Fluxos de trabalho de depuração de um computador remoto (legados)

Este tópico descreve como depurar remoto aplicativos herdados do Windows Workflow Foundation (WF) que são criados com o Designer de fluxo de trabalho herdado do Windows. Use o Designer de fluxo de trabalho herdados quando seu aplicativo precisa para direcionar o .NET Framework versão 3.5 ou o WinFX.

 Quando você instala o Visual Studio, uma das opções de instalação de componente é instalar o Visual Studio depurador para Windows Workflow Foundation (WF). Isso instala os componentes de depuração remota. Esses componentes de depuração remota devem ser instalados no computador que você está definido para depuração remota de fluxo de trabalho.

 Além disso, o assembly que contém a definição de fluxo de trabalho de fluxo de trabalho herdado que você está depurando em um computador remoto deve ser instalado no cachê global de assemblies (GAC) do computador local que você está depurando de. Por exemplo, se um fluxo de trabalho herdado está em execução em um computador remoto e você está depurando-lo do computador local B, a definição de fluxo de trabalho deve estar presente no GAC do computador B. Isso permite que o designer desserializar e exibir no computador B a marcação de fluxo de trabalho do fluxo de trabalho que está executando remotamente no computador A. Para obter mais informações sobre o cache de assembly global, consulte a biblioteca MSDN.

 Depuração remota do Windows Workflow Foundation funciona da mesma forma a depuração remota para outros componentes do Visual Studio. Para obter mais informações, consulte Visual Studio depuração remota na biblioteca MSDN.

## <a name="see-also"></a>Consulte também

- [Depurando fluxos de trabalho herdados](../workflow-designer/debugging-legacy-workflows.md)