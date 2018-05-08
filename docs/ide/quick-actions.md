---
title: Ações Rápidas
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 43198f5722de1bd983991df8ff19b17fcaea9e83
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="quick-actions"></a>Ações Rápidas

As Ações Rápidas permitem refatorar, gerar ou, de outro modo, modificar o código de maneira fácil com uma única ação. As Ações Rápidas estão disponíveis para C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp) e os arquivos de código do Visual Basic. Algumas ações são específicas para uma linguagem e outras se aplicam a todas as linguagens.

É possível usar as Ações rápidas para:

- Aplicar uma correção de código para uma violação de regra do [analisador de código](../code-quality/roslyn-analyzers-overview.md)
- [Suprimir](../code-quality/use-roslyn-analyzers.md) uma violação de regra do analisador de código
- Aplicar uma refatoração (por exemplo, [embutir uma variável temporária](../ide/reference/inline-temporary-variable.md))
- Gerar um código (por exemplo, [introduzir uma variável local](../ide/reference/introduce-local-variable.md))

As Ações Rápidas podem ser aplicadas usando o ícone de Lâmpada ![Ícone de lâmpada pequeno](media/vs2015_lightbulbsmall.png) ou pressionando **Ctrl**+**.** quando o cursor estiver em uma linha de código para a qual uma ação está disponível. Você verá uma lâmpada se houver um rabisco vermelho e o Visual Studio tiver uma sugestão para corrigir o problema. Por exemplo se você tiver um erro indicado por um rabisco vermelho, uma lâmpada aparecerá quando correções estiverem disponíveis para esse erro.

Para qualquer idioma, terceiros podem oferecer diagnósticos e sugestões personalizados, por exemplo, como parte de um SDK, e as lâmpadas do Visual Studio são acesas de acordo com essas regras.

## <a name="to-see-a-light-bulb"></a>Para ver uma lâmpada

1. Em muitos casos, as lâmpadas aparecem espontaneamente ao focalizar o mouse no ponto de um erro ou na margem esquerda do editor ao mover o cursor em uma linha que contém um erro. Quando você vir um rabisco vermelho, poderá focalizar o mouse sobre ele para exibir a lâmpada. Você também poderá fazer com que uma lâmpada seja exibida ao usar o mouse ou o teclado para ir para qualquer lugar da linha em que ocorre o problema.

1. Pressione **Ctrl**+**.** em qualquer lugar de uma linha para invocar a lâmpada e ir diretamente para a lista de possíveis correções.

   ![Lâmpada com o mouse focalizando](../ide/media/vs2015_lightbulb_hover.png)

## <a name="to-see-potential-fixes"></a>Para ver as possíveis correções

Clique na seta para baixo em ou no link **Mostrar possíveis correções** para exibir uma lista de ações rápidas que a lâmpada pode realizar para você.

![Lâmpada expandida](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Consulte também

- [Geração de código no Visual Studio](../ide/code-generation-in-visual-studio.md)
- [Ações Rápidas Comuns](../ide/common-quick-actions.md)
- [Estilos de código e ações rápidas](../ide/code-styles-and-quick-actions.md)
- [Escrever e refatorar o código (C++)](/cpp/ide/writing-and-refactoring-code-cpp)