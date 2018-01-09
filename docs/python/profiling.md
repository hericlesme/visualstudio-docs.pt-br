---
title: "Medindo o desempenho do código do Python no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 07/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: python
ms.openlocfilehash: 525ff73c70b092ca97a9c53759ffa93d55d12c88
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="profiling-python-code"></a>Criação de perfil do código do Python

O Visual Studio dá suporte à criação de perfil de um aplicativo do Python ao usar interpretadores baseados em CPython.

A criação de perfil é iniciada por meio do comando de menu **Analisar > Iniciar Criação de Perfil do Python**, que abre uma caixa de diálogo de configuração:

![Caixa de diálogo de configuração de criação de perfil](media/profiling-start.png)

Quando você seleciona **OK**, o criador de perfil é executado e abre um relatório de desempenho por meio do qual é possível explorar como o tempo é gasto no aplicativo:

![Relatório de desempenho de criação de perfil](media/profiling-results.png)

Para uma demonstração, veja o vídeo [Criação de perfil do Python](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=hb46k6LWE_405918567) (Microsoft Virtual Academy 3min00s).

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Testing-Python-hb46k6LWE_405918567]


## <a name="profiling-for-ironpython"></a>Criação de perfil do IronPython

Como o IronPython não é um interpretador baseado em CPython, o recurso de criação de perfil não funciona.

Em vez disso, use o criador de perfil do .NET do Visual Studio iniciando `ipy.exe` diretamente como o aplicativo de destino, usando os argumentos apropriados para iniciar o script de inicialização. Inclua `-X:Debug` na linha de comando para forçar todo o código do Python a ser depurável e passível à criação de perfil. Esse argumento gera um relatório de desempenho, incluindo o tempo gasto no tempo de execução do IronPython e no código. O código é identificado usando nomes danificados.

Como alternativa, o IronPython tem alguns de seus próprios recursos de criação de perfis internos, mas atualmente não há nenhum visualizador adequado para eles. Consulte [An IronPython Profiler](http://blogs.msdn.com/b/curth/archive/2009/03/29/an-ironpython-profiler.aspx) (Um criador de perfil do IronPython) (blogs do MSDN) para ver o que está disponível.