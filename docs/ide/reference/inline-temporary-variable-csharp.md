---
title: "Substituir uma variável temporária pelo seu valor em C# | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 626224e8ed90196294f7b3ded245bb5272f70595
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="inline-a-temporary-variable-with-c"></a>Insira uma variável temporária com C# #

**O quê:** permite que você remova uma variável temporária e substitua-a pelo seu valor.

**Quando:** o uso da variável temporária dificulta o entendimento do código.

**Por quê:** remover uma variável temporária pode facilitar a leitura do código.

**Como:**

1. realce ou coloque o cursor do texto dentro de uma variável temporária para ser embutida:

   ![Código realçado](media/inline-highlight-cs.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para acionar o menu **Ações e Refatorações Rápidas**.
   * **Mouse**
     * Clique com o botão direito do mouse no código e selecione o menu **Ações e Refatorações Rápidas**.

1. Selecione **Variável temporária embutida** no pop-up da janela Visualização.

   A variável será removida e seus usos substituídos pelo valor da variável imediatamente.

   ![Resultado embutido](media/inline-result-cs.png)

## <a name="see-also"></a>Consulte também

[Refatoração](../refactoring-in-visual-studio.md)