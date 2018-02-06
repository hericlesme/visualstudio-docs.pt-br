---
title: "Introduzir uma variável local - Geração de código (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 6ba9478c09e55df54f94ed93c7a694f798ae76b4
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="introduce-a-local-variable-in-c"></a>Introduzir variável local em C# #

**O quê:** permite gerar imediatamente uma variável local para substituir uma expressão existente.

**Quando:** você tiver um código que poderia ser facilmente reutilizado posteriormente se estivesse em uma variável local.

**Por quê:** você poderia copiar e colar o código várias vezes a fim de usá-lo em vários locais. No entanto, seria melhor executar a operação uma vez, armazenar o resultado em uma variável local e usar a variável local durante todo o processo.

**Como:**

1. Realce a expressão que você deseja atribuir a uma nova variável local.

   ![Código realçado](media/local-highlight-cs.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecione **Introduzir local para (todas as ocorrências da) '*expressão*'** na janela pop-up de visualização, em que *expressão* é o código realçado.
   * **Mouse**
     * Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações** e selecione **Introduzir local para (todas as ocorrências da) '*expressão*'** na janela pop-up de visualização, em que *expressão* é o código realçado.
     * Clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece na margem esquerda se o cursor de texto já estiver na linha com o rabisco vermelho.

   ![Introduzir versão prévia local](media/local-preview-cs.png)

   > [!TIP]
   > Use o link [**Visualizar alterações**](../../ide/preview-changes.md) na parte inferior da janela de visualização para ver todas as alterações que serão feitas antes de fazer sua seleção.

1. A variável local será criada automaticamente com o tipo inferido a partir de seu uso.  Dê um novo nome à nova variável local digitando-o.

   ![Introduzir resultado local](media/local-result-cs.png)

   > [!NOTE]
   > Você pode usar a opção de menu **...todas as ocorrências de...** para substituir todas as instâncias da expressão selecionada encontrada, não apenas aquela especificamente realçada.

## <a name="see-also"></a>Consulte também

[Geração de código](../code-generation-in-visual-studio.md)  
[Visualizar alterações](../../ide/preview-changes.md)
