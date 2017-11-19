---
title: "Variável temporária de embutido - refatoração (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0182179f-f74f-47a2-a1dc-b60c86f9abaf
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e6e9ed28a42aa3d7521a059b668eed8ae1d28b8e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="inline-a-temporary-variable-with-c"></a>Uma variável temporária em linha com c# #
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
[Refatoração (C#)](../refactoring-csharp.md)