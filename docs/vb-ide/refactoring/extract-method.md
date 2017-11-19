---
title: "Extrair método - refatoração (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: 8ad16c15-432b-4b8c-86fd-5f31ad652d24
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractmethod
dev_langs: VB
ms.openlocfilehash: 56e83e6410093467349e4a45a01042133cc53555
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="extract-a-method-in-visual-basic"></a>Extrair um método no Visual Basic
**O que:** permite transformar um fragmento de código em seu próprio método.

**Quando:** tiver um fragmento de código existente em um método que precisa ser chamado a partir de outro método.  

**Motivo:** você poderia copiar/colar esse código, mas que poderia levar a eliminação de duplicação.  É a melhor solução refatorar esse fragmento em seu próprio método que pode ser chamado gratuitamente por qualquer outro método.

**Como:**

1. Realce o código a ser extraído:

   ![Código realçado](media/extractmethod_highlight.png)

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl + R**, em seguida, **Ctrl + M**.  (Observe que o atalho de teclado pode ser diferente com base no perfil selecionado.)
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione **extrair método** do popup da janela de visualização.
   * **Mouse**
     * Selecione **Editar > Refatorar > Extrair método**.
     * O código e selecione **Refatorar > Extrair > Extrair método**.
     * Clique com botão direito do código, selecione o **ações rápidas e refatorações** menu e selecione **extrair método** do popup da janela de visualização.

   O método será criado imediatamente.  A partir daqui, agora você pode renomear o método digitando o novo nome.

   > [!TIP]
   > Também é possível atualizar os comentários e outras cadeias de caracteres para usar esse novo nome, bem como [visualizar as alterações](../../ide/preview-changes.md) salvando antes, usando as caixas de seleção no **Renomear** caixa que aparece na parte superior direita do seu IDE.

   ![Renomeie o método](media/extractmethod_rename.png)

1. Quando estiver satisfeito com a alteração, clique no **aplicar** botão ou pressione **Enter** e as alterações serão confirmadas.

## <a name="see-also"></a>Consulte também  
[Refatoração (Visual Basic)](../refactoring-vb.md)  
[Visualizar alterações](../../ide/preview-changes.md)