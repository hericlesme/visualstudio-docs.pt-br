---
title: "Gerar um método - geração de código (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 683790b4-b68b-42d7-8dc4-a68eca05aa01
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8505f9a4fa8571e0e1c1e45f092d1b0e40c8ee9b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="generate-a-method-in-visual-basic"></a>Gerar um método no Visual Basic
**O que:** permite que você adicione imediatamente um método para uma classe. 

**Quando:** introduzir um novo método e deseja corretamente declará-la, automaticamente.  

**Motivo:** você pode declarar o método e os parâmetros antes de usá-lo, no entanto, esse recurso irá gerar automaticamente a declaração. 

**Como:**

1. Coloque o cursor na linha em que há um rabisco vermelho, indicando que você usou um método que ainda não existe.

   ![Código realçado](media/method_highlight.png)

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione **gerar o método** do popup da janela de visualização.
   * **Mouse**
     * Clique com botão direito e selecione o **ações rápidas e refatorações** menu e selecione **gerar o método** do popup da janela de visualização.
     * Passe o mouse sobre o Rabisco vermelho e clique no ![Lâmpada](media/bulb.png) ícone que aparece.
     * Clique no ![Lâmpada](media/bulb.png) ícone que aparece na margem esquerda, se o cursor de texto já está na linha com o Rabisco vermelho.

   ![Gerar visualização de método](media/method_preview.png)

   >[!TIP]
   >Use o [ **visualizar alterações** ](../../ide/preview-changes.md) link na parte inferior da janela de visualização para ver todas as alterações que serão feitas antes de fazer sua seleção.

1. O método será criado automaticamente com os parâmetros inferidos a partir de seu uso.

   ![Gerar o resultado do método](media/method_result.png)
  
## <a name="see-also"></a>Consulte também  
[Geração de código (Visual Basic)](../code-generation-vb.md)  
[Visualizar alterações](../../ide/preview-changes.md)