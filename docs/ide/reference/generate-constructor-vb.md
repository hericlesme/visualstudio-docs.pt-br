---
title: "Gerar um construtor - Geração de código (Visual Basic) | Microsoft Docs"
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
ms.workload: multiple
ms.openlocfilehash: 891a33b74927d45434c4614dc4c5d7f1533ba4c0
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="generate-a-constructor-in-visual-basic"></a>Gerar um construtor em Visual Basic
**O quê:** permite gerar imediatamente o código para um novo construtor em uma classe. 

**Quando:** você introduz um novo construtor e deseja declará-lo correta e automaticamente.  

**Por quê:** você poderia declarar o construtor antes de usá-lo; no entanto, esse recurso o gerará automaticamente com os parâmetros apropriados. 

**Como:**

1. coloque o cursor na linha em que há um rabisco vermelho indicando que você usou um construtor que ainda não existe.

   ![Código realçado](media/constructor-highlight-vb.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecione **Gerar construtor '*TypeName*'** no pop-up da janela Visualização.
   * **Mouse**
     * Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações** e selecione **Gerar construtor '*TypeName*'** no pop-up da janela Visualização.
     * Passe o mouse sobre o rabisco vermelho e clique no ícone de ![Lâmpada](media/bulb-vb.png) que aparece.
     * Clique no ícone de ![Lâmpada](media/bulb-vb.png) que aparece na margem esquerda se o cursor de texto já estiver na linha com o rabisco vermelho.

   ![Visualização da geração do construtor](media/constructor-preview-vb.png)

   >[!TIP]
   >Use o link [**Visualizar alterações**](../../ide/preview-changes.md) na parte inferior da janela de visualização para ver todas as alterações que serão feitas antes de fazer sua seleção.

1. O construtor será criado automaticamente com quaisquer parâmetros inferidos a partir de seu uso.

   ![Resultado da geração do construtor](media/constructor-result-vb.png)
 
## <a name="see-also"></a>Consulte também

[Geração de código](../code-generation-in-visual-studio.md)  
[Visualizar alterações](../../ide/preview-changes.md)