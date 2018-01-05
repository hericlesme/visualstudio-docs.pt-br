---
title: "Suspensão de recurso automática | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.workload: multiple
ms.openlocfilehash: 0bb8155f2ec1ed6815ac37f1124dfbf57cf838b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="automatic-feature-suspension"></a>Suspensão automática de recursos
Se a memória disponível no sistema cair para 200MB ou menos, o Visual Studio exibe a mensagem a seguir no editor de códigos.  
  
 ![Suspender a análise de solução completa de texto de alerta](../code-quality/media/fsa_alert.png "FSA_Alert")  
  
 Quando o Visual Studio detecta uma condição de memória baixa, suspende automaticamente determinados recursos avançados para ajudá-lo a permanecer estável. Quando isso avançado recurso suspensão aviso é exibido, Visual Studio continuará funcionando como antes, mas seu desempenho será prejudicado ligeiramente.  
  
 Em uma condição de memória baixa, ocorre o seguinte:  
  
-   Análise de solução completa para o Visual c# e Visual Basic está desabilitado.  
  
-   [Coleta de lixo](/dotnet/standard/garbage-collection/index) modo de baixa latência (GC) para Visual c# e Visual Basic são desabilitadas.  
  
-   Os caches do Visual Studio são liberados.  
  
## <a name="improve-visual-studio-performance"></a>Melhorar o desempenho do Visual Studio  
 Para obter dicas e truques sobre como melhorar o desempenho do Visual Studio ao lidar com grandes soluções ou condições de memória baixa, consulte [considerações sobre desempenho para grandes soluções](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).  
  
## <a name="full-solution-analysis-suspended"></a>Análise de solução completa suspenso  
 Por padrão, a análise de solução completa é habilitado para o Visual Basic e desabilitado para o Visual c#. No entanto, em uma condição de memória baixa, análise de solução completa é desabilitada automaticamente para Visual Basic e Visual c#, independentemente de suas definições na caixa de diálogo Opções. No entanto, você pode habilitar novamente análise de solução completa, escolhendo o **reabilitar** botão nas informações da barra quando ela for exibida, selecionando o **habilitar análise de solução completa** caixa de seleção na caixa de diálogo Opções, ou por reiniciar o Visual Studio. A caixa de diálogo Opções sempre mostra a solução atual configurações de análise. Para obter mais informações, consulte [como: habilitar e desabilitar análise de solução completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).  
  
## <a name="gc-low-latency-disabled"></a>GC baixa latência desabilitada  
 Para habilitar o modo de baixa latência da GC novamente, reinicie o Visual Studio.  Por padrão, o Visual Studio permite que o modo de baixa latência GC sempre que você está digitando para garantir que a sua digitação não bloqueie quaisquer operações de GC. No entanto, se uma condição de memória baixa faz com que o Visual Studio exibir o aviso de suspensão automática, modo de baixa latência da GC é desabilitado para a sessão. Reiniciar o Visual Studio habilitar novamente o comportamento de GC padrão. Para obter mais informações, consulte [GCLatencyMode enumeração](http://msdn.microsoft.com/Library/057757a5-cd62-4d13-8a40-370eb7f47c87).  
  
## <a name="visual-studio-caches-flushed"></a>Caches Visual Studio liberados  
 Todos os caches do Visual Studio são esvaziados imediatamente, mas serão iniciado preencher novamente se você continuar a sessão atual de desenvolvimento ou reinicie o Visual Studio. Os caches liberados incluem caches para os recursos a seguir.  
  
-   Localizar todas as referências  
  
-   Navegar para  
  
-   Adicionar usando  
  
 Além disso, os caches usados para operações internas do Visual Studio também estão limpos.  
  
> [!NOTE]
>  O aviso de suspensão do recurso automático ocorre apenas uma vez em uma base por solução, não em uma base por sessão. Isso significa que, se você alterna do Visual Basic para o Visual c# (ou vice-versa) e executar em outra condição de memória baixa, você pode possivelmente receberá outro aviso de suspensão do recurso automática.  
  
## <a name="see-also"></a>Consulte também  
 [Como: habilitar e desabilitar análise de solução completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)   
 [Conceitos básicos da coleta de lixo](/dotnet/standard/garbage-collection/fundamentals)   
 [Considerações sobre desempenho para grandes soluções](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)