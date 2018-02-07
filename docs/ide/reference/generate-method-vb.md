---
title: "Gerar um método - Geração de código (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 683790b4-b68b-42d7-8dc4-a68eca05aa01
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 08e46cb961ecd6511f79410a7424969f2db227ed
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2018
---
# <a name="generate-a-method-in-visual-basic"></a>Gerar um método no Visual Basic
**O quê:** permite que você adicione imediatamente um método a uma classe. 

**Quando:** você introduz um novo método e deseja declará-lo correta e automaticamente.  

**Por quê:** você poderia declarar o método e os parâmetros antes de usá-los; no entanto, esse recurso gerará a declaração automaticamente. 

**Como:**

1. coloque o cursor na linha em que há um rabisco vermelho indicando que você usou um método que ainda não existe.

   ![Código realçado](media/method-highlight-vb.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Gerar método** no pop-up da janela Visualização.
   * **Mouse**
     * Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações** e selecione **Gerar método** no pop-up da janela Visualização.
     * Passe o mouse sobre o rabisco vermelho e clique no ícone de ![Lâmpada](media/bulb-vb.png) que aparece.
     * Clique no ícone de ![Lâmpada](media/bulb-vb.png) que aparece na margem esquerda se o cursor de texto já estiver na linha com o rabisco vermelho.

   ![Visualização de geração do método](media/method-preview-vb.png)

   >[!TIP]
   >Use o link [**Visualizar alterações**](../../ide/preview-changes.md) na parte inferior da janela de visualização para ver todas as alterações que serão feitas antes de fazer sua seleção.

1. O método será criado automaticamente com quaisquer parâmetros inferidos a partir de seu uso.

   ![Resultado da geração do método](media/method-result-vb.png)

## <a name="see-also"></a>Consulte também

[Geração de código](../code-generation-in-visual-studio.md)  
[Visualizar alterações](../../ide/preview-changes.md)