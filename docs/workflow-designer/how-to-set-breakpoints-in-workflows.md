---
title: 'Designer de fluxo de trabalho - como: definir pontos de interrupção em fluxos de trabalho'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: e41b21c9-c061-4358-8e2f-eb5e412864a8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d2ef863bfb899c218a65673236c284bed63aed11
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31973523"
---
# <a name="how-to-set-breakpoints-in-workflows"></a>Como: Definir pontos de interrupção em fluxos de trabalho

Quando você usar o Designer de fluxo de trabalho do Windows, você pode definir pontos de interrupção em seus fluxos de trabalho de gráficos como você faria no código do Visual Basic ou c#. Como esperado, a execução de fluxo de trabalho que ele pare em cada ponto de interrupção esse definido.

 Um ponto de interrupção tem três estados: *pendente*, *associado*, e *erro*. Quando você definir um ponto de interrupção, ele está pendente, e ele é representado por um ícone vermelho contínuo. Quando o tempo de execução carregado o tipo de fluxo de trabalho, transformações limite. Se você especificar um formato incorreto do ponto de interrupção, como um nome de atividade que não é válida, uma janela de erro aparece. O ponto de interrupção é adicionado ainda para a janela de ponto de interrupção, mas é marcado com um pequeno “x”.

> [!NOTE]
> Os pontos de interrupção em fluxos de trabalho chamados não são suportados.

> [!WARNING]
> Certifique-se de que você selecionar a opção **habilitar apenas meu código (somente gerenciado)** do **ferramentas**, **opções**, **depuração** menu antes depure. Se você tiver duas sequências aninhadas dentro de outra sequência e você definir um ponto de interrupção na primeira sequência interna, pressionando **F11** não irá depurar na segunda sequência interna, se o **habilitar apenas meu código (somente gerenciado)** opção não estiver selecionada.

> [!WARNING]
> Os pontos de interrupção em um fluxo de trabalho não obterão a ocorrência se o caminho completo para a propriedade de arquivo XAML não é preciso. O caminho completo do arquivo XAML não é preciso após movido o projeto/solução para outra pasta ou a outro computador. Selecione Ctrl+S para salvar e atualiza a propriedade de caminho completo.

## <a name="to-set-a-breakpoint-on-an-activity-in-the-design-view"></a>Para definir um ponto de interrupção em uma atividade no modo design

1.  Selecione a atividade que você deseja que o depurador para interromper novamente.

2.  Sobre o **depurar** menu, selecione **alternar ponto de interrupção**. Um ícone vermelho aparecerá na borda superior esquerda da atividade.

     Como alternativa, você também pode pressionar o atalho **F9** chave depois de selecionar a atividade ou você pode a atividade e selecione **ponto de interrupção** , em seguida, **Inserir ponto de interrupção**no menu de contexto.

## <a name="see-also"></a>Consulte também

- [Como invocar o depurador de fluxo de trabalho](../workflow-designer/how-to-invoke-the-workflow-debugger.md)
- [Fluxos de trabalho de depuração com o Designer de Fluxo de Trabalho](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)
- [Como depurar XAML com o Designer de Fluxo de Trabalho](../workflow-designer/how-to-debug-xaml-with-the-workflow-designer.md)