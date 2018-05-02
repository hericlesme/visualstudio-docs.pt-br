---
title: Recolher e expandir as regiões do código no Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 62e6d5c7667bf697eeb190d69a996886fbee643f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="outlining"></a>Estrutura de tópicos

Você pode optar por ocultar a exibição de algum código recolhendo uma região do código para que ele apareça sob um sinal de adição (**+**). Você expande uma região recolhida clicando no sinal de adição. Se for um usuário de teclado, você poderá escolher **Ctrl**+**M**+**M** para recolher e expandir. Você também pode recolher uma região de estrutura de tópicos clicando duas vezes em qualquer linha na região na margem da estrutura de tópicos, que aparece à esquerda do código. Você pode ver o conteúdo de uma região recolhida como uma dica de ferramenta quando focaliza a região recolhida.

As regiões na margem da estrutura de tópicos também são realçadas quando você focaliza a margem com o mouse. A cor de realce padrão pode parecer bastante esmaecida em algumas configurações de cor. Você pode alterá-la em **Ferramentas** > **Opções** > **Ambiente** > **Fontes e Cores**  >  **Região recolhível**.

Quando você trabalha no código de estrutura de tópicos, pode expandir as seções nas quais deseja trabalhar, recolhê-las quando terminar e passar para outras seções. Quando você não quiser que a estrutura de tópicos seja exibida, você pode usar o comando **Interromper Estrutura de Tópicos** para remover as informações de estrutura de tópicos sem afetar o código subjacente.

Os comandos **Desfazer** e **Refazer** no menu **Editar** afetam essas ações. As operações de **Copiar**, **Recortar**, **Colar** e do tipo "arrastar e soltar" retêm informações de estrutura de tópico, mas não o estado da região recolhível. Por exemplo, quando você copia uma região recolhida, a operação **Colar** colará o texto copiado como uma região expandida.

> [!CAUTION]
> Quando você altera uma região de estrutura de tópicos, a estrutura de tópicos pode ser perdida. Por exemplo, exclusões ou operações de Localizar e Substituir podem apagar o fim da região.

Os comandos a seguir podem ser encontrados no submenu **Editar** > **Estrutura de Tópicos**.

|||
|-|-|
|Ocultar Seleção|(**Ctrl**+**M**, **Ctrl**+**H**) – recolhe um bloco de código selecionado que normalmente não estaria disponível para a estrutura de tópicos, por exemplo, um bloco `if`. Para remover a região personalizada, use **Interromper Ocultação Atual** (ou **Ctrl**+**M**, **Ctrl**+**U**). Não disponível no Visual Basic.|
|Ativar/Desativar Expansão da Estrutura de Tópicos|– Reverte o estado atual oculto ou expandido da seção de estrutura de tópicos mais interna quando o cursor está em uma seção recolhida aninhada.|
|Ativar/Desativar Estrutura de Tópicos para Tudo|(**Ctrl**+**M**, **Ctrl**+**L**) – define todas as regiões para o mesmo estado recolhido ou expandido. Se algumas regiões estiverem expandidas e algumas estiverem recolhidas, as regiões recolhidas serão expandidas.|
|Interromper Estrutura de Tópicos|(**Ctrl**+**M**, **Ctrl**+**P**) – remove todas as informações de estrutura de tópicos do documento inteiro.|
|Interromper Ocultação Atual|(**Ctrl**+**M**, **Ctrl**+**U**) – remove as informações de estrutura de tópicos da região definida pelo usuário selecionada no momento. Não disponível no Visual Basic.|
|Recolher para Definições|(**Ctrl**+**M**, **Ctrl**+**O**) – recolhe os membros de todos os tipos.|
|Recolher bloco:\<limite lógico>|(Visual C++) Recolhe uma região na função que contém o ponto de inserção. Por exemplo, se o ponto de inserção estiver dentro de um loop, o loop será ocultado.|
|Recolher tudo: \<estruturas lógicas>|(Visual C++) Recolhe todas as estruturas de dentro da função.|

Você também pode usar o SDK do Visual Studio para definir as regiões de texto que deseja expandir ou recolher. Consulte [Instruções passo a passo: estrutura de tópicos](../extensibility/walkthrough-outlining.md).

## <a name="see-also"></a>Consulte também

- [Escrever o código no editor](../ide/writing-code-in-the-code-and-text-editor.md)
