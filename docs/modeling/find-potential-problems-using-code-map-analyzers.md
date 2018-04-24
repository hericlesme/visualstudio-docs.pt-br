---
title: Encontrar possíveis problemas usando analisadores de mapas de códigos
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: a282c192b06f878279f567673469d223a71b8d89
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2018
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Encontrar possíveis problemas usando analisadores de mapa de códigos
Execute analisadores em mapas de código para ajudá-lo a identificar o código que pode ser excessivamente complexas ou que pode ser aperfeiçoado. Por exemplo, você pode usar esses analisadores:

|**Para localizar o código que tem**|**Examine essas áreas para ver se**|
|-------------------------------|--------------------------------------------|
|Loops ou dependências circulares|Você pode simplificá-los e considere se você pode interromper esses ciclos.|
|Número excessivo de dependências|Eles são realizar muitas funções ou para determinar o impacto das alterações nessas áreas. Um mapa de código bem formado mostrará um número mínimo de dependências. Para tornar o código mais fácil de manter, alterar, testar e reutilizar, considere se refatorar essas áreas para que eles são mais claramente definidos ou se é possível mesclar o código que executa funções semelhantes.|
|Sem dependências|Eles são necessários ou se você deve remover esse código.|

## <a name="analyze-code-maps"></a>Analisar o mapa de códigos

1.  Na barra de ferramentas do mapa, escolha **Layout**, **analisadores**e, em seguida, o analisador que você deseja executar:

    |**Analisador**|**Para identificar nós que**|
    |------------------|--------------------------------|
    |**Analisador de referências circulares**|Tem dependências circulares entre si. **Observação:** dependências circulares que estão no **genéricos** grupo não são mostrados no mapa quando você expande o grupo.|
    |**Localizar o analisador de Hubs**|Estão na 25% principais de nós conectados altamente<br /><br /> **Para ocultar todos os outros nós no mapa**<br /><br /> -Abra o menu de atalho para o mapa, escolha **avançado**, **selecione**, **ocultar desmarcado**.<br />     O mapa oculta os nós não selecionados, e o Analisador identifica novos nós como hubs.|
    |**Analisador de nós não referenciada**|Não tem referências de todos os outros nós. **Cuidado:** Verifique se cada um desses casos antes supondo que o código não é usado. Não foi encontradas determinadas dependências como dependências XAML e tempo de execução estaticamente no código.|

 Analisadores de mapa de código continue em execução depois que você aplicá-los. Se você alterar o mapa, analisadores aplicados serão automaticamente reprocessar o mapa atualizado. Para interromper a execução de um analisador, na barra de ferramentas do mapa, escolha **Layout**, **analisadores**. Desative o analisador selecionado.

> [!TIP]
> Se você tiver um mapa muito grande, executar um analisador pode causar um limite de exceção de memória. Se isso ocorrer, edite o mapa para reduzir o escopo ou gerar uma menor e, em seguida, executar o analisador.

## <a name="see-also"></a>Consulte também

- [Mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md)
- [Usar mapas de códigos para depurar aplicativos](../modeling/use-code-maps-to-debug-your-applications.md)
- [Mapear métodos na pilha de chamadas durante a depuração](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
