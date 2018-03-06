---
title: "Medindo o desempenho do código do Python no Visual Studio | Microsoft Docs"
description: "Como usar o criador de perfil do Visual Studio para verificar o desempenho do código Python ao usar interpretadores baseados em CPython."
ms.custom: 
ms.date: 01/09/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: c946f9d0fea5192f75d2fd0a9865827b6027ef50
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2018
---
# <a name="profiling-python-code"></a>Criação de perfil do código do Python

Você pode criar um perfil de um aplicativo Python ao usar interpretadores baseados em CPython. (Confira [Matriz de recursos – criação de perfil](overview-of-python-tools-for-visual-studio.md#matrix-profiling) para saber a disponibilidade desse recurso para diferentes versões do Visual Studio.)

A criação de perfil é iniciada por meio do comando de menu **Analisar > Iniciar Criação de Perfil do Python**, que abre uma caixa de diálogo de configuração:

![Caixa de diálogo de configuração de criação de perfil](media/profiling-start.png)

Quando você seleciona **OK**, o criador de perfil é executado e abre um relatório de desempenho por meio do qual é possível explorar como o tempo é gasto no aplicativo:

![Relatório de desempenho de criação de perfil](media/profiling-results.png)

|   |   |
|---|---|
| ![ícone de câmera para vídeo](../install/media/video-icon.png "Assistir a um vídeo") | [Assista a um vídeo (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Profiling-Python-s6FoC6LWE_1005918567) para uma demonstração da criação de perfil do Python (3min00s).|

> [!Note]
> No momento, o Visual Studio oferece suporte somente a esse nível de criação de perfil de aplicativo completo, mas certamente queremos ouvir seus comentários sobre recursos futuros. Use o botão [**Fornecer comentários sobre o produto**](#feedback) na parte inferior desta página.

## <a name="profiling-for-ironpython"></a>Criação de perfil do IronPython

Como o IronPython não é um interpretador baseado em CPython, o recurso de criação de perfil não funciona.

Em vez disso, use o criador de perfil do .NET do Visual Studio iniciando `ipy.exe` diretamente como o aplicativo de destino, usando os argumentos apropriados para iniciar o script de inicialização. Inclua `-X:Debug` na linha de comando para garantir que todo o seu código Python possa ser depurado e seja passível à criação de perfil. Esse argumento gera um relatório de desempenho, incluindo o tempo gasto no tempo de execução do IronPython e no código. O código é identificado usando nomes danificados.

Como alternativa, o IronPython tem alguns de seus próprios recursos de criação de perfis internos, mas atualmente não há nenhum visualizador adequado para eles. Consulte [An IronPython Profiler](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx) (Um criador de perfil do IronPython) (blogs do MSDN) para ver o que está disponível.