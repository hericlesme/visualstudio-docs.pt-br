---
title: "Gerar um campo, propriedade ou local - geração de código (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c11888e0-31b1-44cc-9037-98d3f8b3623b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8e23dfa2b482a16d70ef71614ba35f9b20523aeb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="generate-a-field-property-or-local-in-visual-basic"></a>Gerar um campo, propriedade ou local no Visual Basic
**O que:** permite gerar imediatamente o código para um campo não declarado anteriormente, a propriedade ou o local. 

**Quando:** introduz um novo campo, propriedade ou local durante a digitação e deseja corretamente declará-la, automaticamente.  

**Motivo:** você pode declarar o campo, propriedade ou local antes de usá-lo, no entanto, esse recurso será gerar a declaração e digite automaticamente. 

**Como:**

1. Coloque o cursor na linha em que há um rabisco vermelho, indicando que você usou um campo, local ou uma propriedade que ainda não existe.

   ![Código realçado](media/field_highlight.png)

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione  **gerar variável '*nome*' > Gerar campo/propriedade/local * * do popup da janela de visualização.
   * **Mouse**
     * Clique com botão direito e selecione o **ações rápidas e refatorações** menu e selecione  **gerar variável '*nome*' > Gerar campo/propriedade/local * * da visualização janela pop-up.
     * Passe o mouse sobre o Rabisco vermelho e clique no ![Lâmpada](media/bulb.png) ícone que aparece.
     * Clique no ![Lâmpada](media/bulb.png) ícone que aparece na margem esquerda, se o cursor de texto já está na linha com o Rabisco vermelho.

   ![Gerar visualização de campo/propriedade/local](media/field_preview.png)

   >[!TIP]
   >Use o [ **visualizar alterações** ](../../ide/preview-changes.md) link na parte inferior da janela de visualização para ver todas as alterações que serão feitas antes de fazer sua seleção.

1. O campo, propriedade ou local será criado automaticamente com o tipo inferido de seu uso.

   ![Gerar resultados de campo/propriedade/local](media/field_result.png)

## <a name="see-also"></a>Consulte também  
[Geração de código (Visual Basic)](../code-generation-vb.md)  
[Visualizar alterações](../../ide/preview-changes.md)