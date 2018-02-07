---
title: "Implementar uma classe abstrata - Geração de código (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96cfed7f-f090-4369-8a85-2dcd4c7cf12b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: f089ffbe33d4a36e84d6d39abb3b3db3c4b2aeb7
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2018
---
# <a name="implement-an-abstract-class-in-c"></a>Implementar uma classe abstrata em C# #
**O quê:** permite gerar imediatamente o código necessário para implementar uma classe abstrata. 

**Quando:** você deseja herdar de uma classe abstrata.  

**Por quê:** você pode implementar manualmente todos os membros abstratos um por um; no entanto, esse recurso gerará automaticamente todas as assinaturas de método. 

**Como:**

1. coloque o cursor na linha em que há um rabisco vermelho indicando que você herdou de uma classe abstrata, mas não implementou todos os membros necessários.

   ![Código realçado](media/abstract-highlight-cs.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Implementar Classe Abstrata** no pop-up da janela Visualização.
   * **Mouse**
     * Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações** e selecione **Implementar Classe Abstrata** no pop-up da janela Visualização.
     * Passe o mouse sobre o rabisco vermelho e clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece.
     * Clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece na margem esquerda se o cursor de texto já estiver na linha com o rabisco vermelho.

   ![Visualização da implementação de classe](media/abstract-preview-cs.png)

   >[!TIP]
   >Use o link [**Visualizar alterações**](../../ide/preview-changes.md) na parte inferior da janela de visualização para ver todas as alterações que serão feitas antes de fazer sua seleção.
   >
   >Além disso, você pode usar os links **Documento**, **Projeto** e **Solução** na parte inferior da janela de visualização para criar as assinaturas de método corretas em várias classes que herdam da classe abstrata.

1. As assinaturas de método abstratas serão criadas automaticamente, prontas para serem implementadas.

   ![Resultado da implementação de classe](media/abstract-result-cs.png)

## <a name="see-also"></a>Consulte também

[Geração de código](../code-generation-in-visual-studio.md)  
[Visualizar alterações](../../ide/preview-changes.md)
