---
title: "Gerar um construtor - geração de código (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0380076319a80ba85aa59c388959baece9008e94
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2017
---
# <a name="generate-a-constructor-in-visual-basic"></a>Gerar um construtor no Visual Basic
**O que:** permite gerar imediatamente o código para um novo construtor em uma classe. 

**Quando:** introduz um novo construtor e deseja corretamente declará-la, automaticamente.  

**Motivo:** você pode declarar o construtor antes de usá-lo, no entanto, esse recurso irá gerar, com os parâmetros adequados, automaticamente. 

**Como:**

1. Coloque o cursor na linha em que há um rabisco vermelho, indicando que você usou um construtor que ainda não existe.

   ![Código realçado](media/constructor_highlight.png)

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione  **gerar construtor '*TypeName*' * * do popup da janela de visualização.
   * **Mouse**
     * Clique com botão direito e selecione o **ações rápidas e refatorações** menu e selecione  **gerar construtor '*TypeName*' * * do popup da janela de visualização.
     * Passe o mouse sobre o Rabisco vermelho e clique no ![Lâmpada](media/bulb.png) ícone que aparece.
     * Clique no ![Lâmpada](media/bulb.png) ícone que aparece na margem esquerda, se o cursor de texto já está na linha com o Rabisco vermelho.

   ![Gerar visualização de construtor](media/constructor_preview.png)

   >[!TIP]
   >Use o [ **visualizar alterações** ](../../ide/preview-changes.md) link na parte inferior da janela de visualização para ver todas as alterações que serão feitas antes de fazer sua seleção.

1. O construtor será criado automaticamente com os parâmetros inferidos a partir de seu uso.

   ![Gerar resultados de construtor](media/constructor_result.png)
  
## <a name="see-also"></a>Consulte também  
[Geração de código (Visual Basic)](../code-generation-vb.md)  
[Visualizar alterações](../../ide/preview-changes.md)