---
title: Suspensão automática de recursos no Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: d75c02bf6b817d03492a15b1f827f94eaaf3e306
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="automatic-feature-suspension"></a>Suspensão automática de recursos

Se a memória disponível no sistema cair para 200 MB ou menos, o Visual Studio exibe a mensagem a seguir no editor de código:

![Suspender a análise de solução completa de texto de alerta](../code-quality/media/fsa_alert.png)

Quando o Visual Studio detecta uma condição de memória baixa, suspende automaticamente determinados recursos avançados para ajudá-lo a permanecer estável. O Visual Studio continuará a funcionar como antes, mas o desempenho é degradado.

Em uma condição de pouca memória, as seguintes ações ocorrem:

- Análise de solução completa para o Visual c# e Visual Basic está desabilitado.

- [Coleta de lixo](/dotnet/standard/garbage-collection/index) modo de baixa latência (GC) para Visual c# e Visual Basic está desabilitado.

- Os caches do Visual Studio são liberados.

## <a name="improve-visual-studio-performance"></a>Melhorar o desempenho do Visual Studio

Para obter dicas e truques sobre como melhorar o desempenho do Visual Studio ao lidar com grandes soluções ou condições de memória baixa, consulte [considerações sobre desempenho para grandes soluções](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Análise de solução completa suspenso

Por padrão, a análise de solução completa é habilitado para o Visual Basic e desabilitado para o Visual c#. No entanto, em uma condição de memória baixa, análise de solução completa é desabilitada automaticamente para Visual Basic e Visual c#, independentemente de suas definições na caixa de diálogo Opções. No entanto, você pode habilitar novamente análise de solução completa, escolhendo o **reabilitar** botão nas informações da barra quando ela for exibida, selecionando o **habilitar análise de solução completa** caixa de seleção na caixa de diálogo Opções, ou por reiniciar o Visual Studio. A caixa de diálogo Opções sempre mostra a solução atual configurações de análise. Para obter mais informações, consulte [como: habilitar e desabilitar análise de solução completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>GC baixa latência desabilitada

Para habilitar o modo de baixa latência da GC novamente, reinicie o Visual Studio. Por padrão, o Visual Studio permite que o modo de baixa latência GC sempre que você está digitando para garantir que a sua digitação não bloqueie quaisquer operações de GC. No entanto, se uma condição de memória baixa faz com que o Visual Studio exibir o aviso de suspensão automática, modo de baixa latência da GC é desabilitado para a sessão. Reiniciar o Visual Studio habilita novamente o comportamento de GC padrão. Para obter mais informações, consulte <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Caches Visual Studio liberados

Se você continuar a sessão atual de desenvolvimento ou reinicie o Visual Studio, todos os caches do Visual Studio são esvaziados imediatamente, mas começa a preencher novamente. Os caches liberados incluem caches para os seguintes recursos:

- Localizar todas as referências

- Navegar para

- Adicionar usando

Além disso, os caches usados para operações internas do Visual Studio também estão limpos.

> [!NOTE]
> O aviso de suspensão do recurso automático ocorre apenas uma vez em uma base por solução, não em uma base por sessão. Isso significa que, se você alterna do Visual Basic para o Visual c# (ou vice-versa) e executar em outra condição de memória baixa, você pode possivelmente receberá outro aviso de suspensão do recurso automática.

## <a name="see-also"></a>Consulte também

- [Como: habilitar e desabilitar análise de solução completa](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Conceitos básicos da coleta de lixo](/dotnet/standard/garbage-collection/fundamentals)
- [Considerações sobre desempenho para grandes soluções](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)