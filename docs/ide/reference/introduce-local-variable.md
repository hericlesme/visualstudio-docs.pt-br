---
title: "Introduzir uma variável local no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 997220d3b1a7305f84f61ee5fd4c205d1157f1b2
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
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
     - Pressione **Ctrl +.** para acionar o menu **Ações e Refatorações Rápidas**.
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

[Geração de código](../code-generation-in-visual-studio.md)  
[Visualizar alterações](../../ide/preview-changes.md)
