---
title: Introduzir uma variável local no Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: d028d89f149a2fe444508d09086f6bec2408889e
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510995"
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Introduzir uma variável local no Visual Studio

Esta geração de código aplica-se a:

- C#

- Visual Basic

**O quê:** permite gerar imediatamente uma variável local para substituir uma expressão existente.

**Quando:** você tiver um código que poderia ser facilmente reutilizado posteriormente se estivesse em uma variável local.

**Por quê:** você poderia copiar e colar o código várias vezes a fim de usá-lo em vários locais. No entanto, seria melhor executar a operação uma vez, armazenar o resultado em uma variável local e usar a variável local durante todo o processo.

## <a name="how-to"></a>Como fazer

1. Realce a expressão que você deseja atribuir a uma nova variável local.

   - C#:

    ![Código em C# realçado](media/local-highlight-cs.png)

   - Visual Basic:

    ![Código em VB realçado](media/local-highlight-vb.png)

1. Depois, siga um destes procedimentos:

   - **Teclado**
     - Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
     - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
     - Clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece na margem esquerda se o cursor de texto já estiver na linha com o rabisco vermelho.

   ![Introduzir versão prévia local](media/local-preview-cs.png)

1. Selecione **Introduzir local para a (todas as ocorrências da) '*expressão*'** no menu suspenso.

   > [!TIP]
   > Use o link **Visualizar alterações** na parte inferior da janela de visualização [para ver todas as alterações](../../ide/preview-changes.md) que serão feitas antes de fazer sua seleção.

   A variável local é criada, com o tipo inferido com base em seu uso. Forneça um novo nome à nova variável local.

   - C#:

      ![Resultado da implementação da interface em C#](media/local-result-cs.png)

   - Visual Basic:

      ![Resultado da implementação da interface em VB](media/local-result-vb.png)

   > [!NOTE]
   > Você pode usar a opção de menu **...todas as ocorrências de...** para substituir todas as instâncias da expressão selecionada, não somente a que foi especificamente realçada.

## <a name="see-also"></a>Consulte também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)