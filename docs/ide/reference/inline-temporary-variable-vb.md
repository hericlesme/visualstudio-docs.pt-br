---
title: "Substituir uma variável temporária pelo seu valor em Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 7553a67892322a1acb2db33d7a16b399b6f0b23a
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2018
---
# <a name="inline-a-temporary-variable-in-visual-basic"></a>Embutir uma variável temporária em Visual Basic

**O quê:** permite que você remova uma variável temporária e substitua-a pelo seu valor.

**Quando:** o uso da variável temporária dificulta o entendimento do código.

**Por quê:** remover uma variável temporária pode facilitar a leitura do código.

**Como:**

1. realce ou coloque o cursor do texto dentro de uma variável temporária para ser embutida:

   ![Código realçado](media/inline-highlight-vb.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para acionar o menu **Ações e Refatorações Rápidas**.
   * **Mouse**
     * Clique com o botão direito do mouse no código e selecione o menu **Ações e Refatorações Rápidas**.

1. Selecione **Variável temporária embutida** no pop-up da janela Visualização.

   A variável será removida e seus usos substituídos pelo valor da variável imediatamente.

   ![Resultado embutido](media/inline-result-vb.png)

## <a name="see-also"></a>Consulte também

[Refatoração](../refactoring-in-visual-studio.md)