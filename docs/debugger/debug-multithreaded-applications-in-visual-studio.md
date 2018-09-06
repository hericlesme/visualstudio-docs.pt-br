---
title: Depurar aplicativos multi-threaded no Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 46f165896947f541a7f7be2c48658b83dfd3d102
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35670226"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Depurar aplicativos multithread no Visual Studio
Um thread é uma sequência de instruções para que o sistema operacional aloque tempo no processador. Cada processo que está em execução no sistema operacional consiste em pelo menos um thread. Os processos que têm mais de um thread são chamados multithread.  
  
Os computadores com vários processadores, processadores de vários núcleos ou processos de hyperthreading podem executar vários threads ao mesmo tempo. O processamento paralelo de vários threads pode aumentar melhorar o desempenho do programa, mas também pode tornar a depuração mais difícil porque apresenta a necessidade de manter controle de vários threads.  
  
Além disso, o multithreading apresenta alguns novos tipos de bugs potenciais. Geralmente, dois ou mais threads precisam acessar o mesmo recurso, mas apenas um thread pode acessar com segurança o recurso de cada vez. Alguma forma de exclusão mútua é necessário para certificar-se de que apenas um thread está acessando o recurso de cada vez. Se a exclusão mútua for executada incorretamente, pode criar uma *deadlock* condição em que nenhum thread possa executar. Deadlocks podem ser um problema particularmente difícil de depurar.

Visual Studio fornece ferramentas diferentes para uso na depuração de aplicativos multithreaded.

- Para threads, as ferramentas principais para depurar threads são a **Threads** janela, marcadores de thread em janelas de origem **pilhas paralelas** janela **inspeção paralela** janela, e o **local de depuração** barra de ferramentas. Para saber mais sobre o **Threads** janela e **local de depuração** barra de ferramentas, consulte [passo a passo: depurar usando a janela Threads](../debugger/how-to-use-the-threads-window.md). Para saber como usar o **pilhas paralelas** e **inspeção paralela** windows, consulte [começar a depurar um aplicativo multi-threaded](../debugger/get-started-debugging-multithreaded-apps.md). Os dois tópicos mostram como usar marcadores de thread.
  
- Para o código que usa o [tarefa TPL (biblioteca paralela)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) ou o [tempo de execução de simultaneidade](/cpp/parallel/concrt/concurrency-runtime/), são as ferramentas principais para depurar o **pilhas paralelas** janela, o **Inspeção paralela** janela e o **tarefas** janela (a **tarefas** janela também dá suporte a JavaScript). Para começar, consulte [instruções passo a passo: depurando um aplicativo paralelo](../debugger/walkthrough-debugging-a-parallel-application.md) e [passo a passo: depurando um aplicativo C++ AMP](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application). 

- Para depurar threads na GPU, a principal ferramenta é o **Threads da GPU** janela. Ver [como: usar a janela Threads da GPU](../debugger/how-to-use-the-gpu-threads-window.md).  

- Para processos, as ferramentas principais são as **anexar ao processo** caixa de diálogo, o **processos** janela e o **local de depuração** barra de ferramentas.  
  
O Visual Studio também fornece os pontos de interrupção avançados e pontos de controle, que podem ser muito úteis quando você depura aplicativos multissegmentados. Você pode usar condições de ponto de interrupção e filtros para colocar pontos de interrupção em threads individuais. Ver [usando pontos de interrupção](../debugger/using-breakpoints.md). 
  
Depurar um aplicativo com vários thread que tenha uma interface de usuário pode ser especialmente difícil. Nesse caso, você poderá considerar a execução do aplicativo em um segundo computador e o uso da depuração remota. Para obter informações, consulte [depuração remota](../debugger/remote-debugging.md).  
  
## <a name="in-this-section"></a>Nesta seção
 [Introdução ao depurar um aplicativo multithreaded](../debugger/get-started-debugging-multithreaded-apps.md).  
 Um tour guiado dos recursos de depuração com ênfase nos recursos na **pilhas paralelas** janela e **inspeção paralela** janela.

 [Ferramentas para depurar Threads e processos](../debugger/debug-threads-and-processes.md)  
 Lista os recursos das ferramentas para depurar threads e processos.  
  
 [Depurar vários processos](../debugger/debug-multiple-processes.md)  
 Explica como depurar vários processos.

 [Passo a passo: Depurar usando a janela Threads](../debugger/how-to-use-the-threads-window.md).  
 Passo a passo que mostra como usar o **Threads** janela e o **local de depuração** barra de ferramentas. 

 [Passo a passo: Depurar um aplicativo paralelo](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Passo a passo que mostra como usar o **pilhas paralelas** e **tarefas** windows.  
  
 [Como mudar para outro thread durante a depuração](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 Três maneiras para alternar o contexto de depuração para outro segmento.  
  
 [Como sinalizar e remover sinalizador de threads](../debugger/how-to-flag-and-unflag-threads.md)  
 Marque ou sinalize threads aos quais você deseja dar atenção especial durante a depuração.    
  
 [Como depurar em um cluster de alto desempenho](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 Técnicas para depurar um aplicativo executado em um conjunto de alto desempenho.  

 [Dicas para threads de depuração no código nativo](../debugger/tips-for-debugging-threads-in-native-code.md)  
 Técnicas simples que podem ser úteis para depurar threads nativos. 

 [Como definir um nome de thread em código nativo](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 Atribua ao thread um nome que você vê na **Threads** janela.  
  
 [Como definir um nome de thread em código gerenciado](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 Atribua ao thread um nome que você vê na **Threads** janela. 
  
## <a name="related-sections"></a>Seções relacionadas  
 [Usando pontos de interrupção](../debugger/using-breakpoints.md)

 - Use filtros ou condições de ponto de interrupção quando você deseja depurar um segmento individual.  
  
 - Os pontos de controle permitem que você rastreie a execução do programa sem interrupções. Isso pode ser útil para estudar problemas, como deadlocks.  
  
 [Threading](/dotnet/standard/threading/index)  
 Conceitos de segmentação na programação de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], incluindo o código de exemplo.  
  
 [Multithreading em componentes](http://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)  
 Como usar multithreading em componentes de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 [Suporte de multithreading para código anterior (Visual C++)](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)  
 Conceitos de segmentação e código de exemplo para programadores de C++ que usam o MFC.  
  
## <a name="see-also"></a>Consulte também  
 [Depurar Threads e processos](../debugger/debug-threads-and-processes.md)   
 [Depuração remota](../debugger/remote-debugging.md)