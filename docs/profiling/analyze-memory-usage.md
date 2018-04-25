---
title: Analisar o uso de memória no Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f29251a7b8f5e38e5b74a6aabd17ae0ccfec7651
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/19/2018
---
# <a name="analyze-memory-usage"></a>Analisar o uso de memória
Use a ferramenta de diagnóstico **Uso de Memória** integrada no depurador para localizar perdas de memória e uso de memória ineficiente. A ferramenta Uso de Memória permite que você tire um ou mais *instantâneos* do heap de memória gerenciada e do heap de memória nativa. Você pode coletar instantâneos de aplicativos .NET, nativos ou mistos (.NET e nativos).  
  
-   É possível analisar um único instantâneo para compreender o impacto relativo dos tipos de objeto sobre o uso da memória e encontrar o código no aplicativo que usa a memória de maneira ineficiente.  
  
-   Também é possível comparar (diff) dois instantâneos de um aplicativo para encontrar áreas no código que causam o aumento do uso da memória com o passar do tempo.  

Para obter instruções detalhadas, consulte o tutorial [Analisar o uso de memória](../profiling/memory-usage.md). Para analisar o uso de memória sem anexar o depurador, consulte [Uso de memória sem o depurador](memory-usage-without-debugging2.md).
  
## <a name="blogs-and-videos"></a>Blogs e vídeos  

|         |         |
|---------|---------|
|  ![ícone de câmera para vídeo](../install/media/video-icon.png "Assistir a um vídeo")  |    [Assista a um vídeo](https://mva.microsoft.com/en-US/training-courses-embed/getting-started-with-visual-studio-2017-17798/Profiling-with-Diagnostics-Tools-in-Visual-Studio-2017-daHnzMD6D_9211787171) sobre como usar as ferramentas de diagnóstico que mostra como analisar o uso de memória e o uso de CPU no Visual Studio 2017. |

 [Analyze CPU and Memory While Debugging](https://blogs.msdn.microsoft.com/visualstudio/2016/02/15/analyze-cpu-memory-while-debugging/) (Analisar a CPU e a memória durante a depuração)  
  
 [Visual C++ Blog: Memory Profiling in Visual C++ 2015](https://blogs.msdn.microsoft.com/vcblog/2015/10/21/memory-profiling-in-visual-c-2015/) (Blog do Visual C++: Criação de perfil de memória no Visual C++ 2015)  

## <a name="see-also"></a>Consulte também
 [Criação de perfis no Visual Studio](../profiling/index.md)  
 [Tour pelos recursos de criação de perfil](../profiling/profiling-feature-tour.md)