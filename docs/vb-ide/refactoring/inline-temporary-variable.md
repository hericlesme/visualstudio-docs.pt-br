---
title: "Variável temporária embutida - refatoração (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a63d6407-5acb-4d5f-8c0e-ecedddc07177
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 574a1a41464ede08571e1c0201618d666fa7ad92
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="inline-a-temporary-variable-in-visual-basic"></a>Embutido uma variável temporária no Visual Basic
**O que:** permite que você remova o uso de uma variável temporária e substituí-lo com o código real.

**Quando:** o uso da variável temporária torna mais difícil de entender o código.  

**Motivo:** a remoção de uma variável temporária pode tornar o código mais fácil de ler em certas situações

**Como:**

1. Realçar ou coloque o cursor do texto dentro de uma variável temporária para ser embutido:

   ![Código realçado](media/inline_highlight.png)

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione **variável temporária embutida** do popup da janela de visualização.
   * **Mouse**
     * Clique com botão direito do código, selecione o **ações rápidas e refatorações** menu e selecione **variável temporária embutida** do popup da janela de visualização.

   A variável será removida e seus usos substituído pelo valor da variável imediatamente.

   ![Resultados inline](media/inline_result.png)

## <a name="see-also"></a>Consulte também
[Refatoração (Visual Basic)](../refactoring-vb.md)