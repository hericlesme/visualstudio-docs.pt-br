---
title: "Implementar uma classe abstrata - Geração de código (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96cfed7f-f090-4369-8a85-2dcd4c7cf12b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 135c1edc6719c567e21496f047af45b7ce311d13
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="implement-an-abstract-class-in-visual-basic"></a>Implementar uma classe abstrata no Visual Basic
**O quê:** permite gerar imediatamente o código necessário para implementar uma classe abstrata. 

**Quando:** você deseja herdar de uma classe abstrata.  

**Por quê:** você pode implementar manualmente todos os membros abstratos um por um; no entanto, esse recurso gerará automaticamente todas as assinaturas de método. 

**Como:**

1. coloque o cursor na linha em que há um rabisco vermelho indicando que você herdou de uma classe abstrata, mas não implementou todos os membros necessários.

   ![Código realçado](media/abstract-highlight-vb.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Implementar Classe Abstrata** no pop-up da janela Visualização.
   * **Mouse**
     * Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações** e selecione **Implementar Classe Abstrata** no pop-up da janela Visualização.
     * Passe o mouse sobre o rabisco vermelho e clique no ícone de ![Lâmpada](media/bulb-vb.png) que aparece.
     * Clique no ícone de ![Lâmpada](media/bulb-vb.png) que aparece na margem esquerda se o cursor de texto já estiver na linha com o rabisco vermelho.

   ![Visualização da implementação de classe](media/abstract-preview-vb.png)

   >[!TIP]
   >Use o link [**Visualizar alterações**](../../ide/preview-changes.md) na parte inferior da janela de visualização para ver todas as alterações que serão feitas antes de fazer sua seleção.
   >
   >Além disso, você pode usar os links **Documento**, **Projeto** e **Solução** na parte inferior da janela de visualização para criar as assinaturas de método corretas em várias classes que herdam da classe abstrata.

1. As assinaturas de método abstratas serão criadas automaticamente, prontas para serem implementadas.

   ![Resultado da implementação de classe](media/abstract-result-vb.png)

## <a name="see-also"></a>Consulte também

[Geração de código](../code-generation-in-visual-studio.md)  
[Visualizar alterações](../../ide/preview-changes.md)