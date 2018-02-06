---
title: "Implementar uma interface - Geração de código (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bebff2ad-25b6-4adc-8762-60d23bdd639a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 908e11da78b2a83fb3da23d28b5cc52613f7b0f2
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="implement-an-interface-in-c"></a>Implementar uma interface no C# #
**O quê:** permite gerar imediatamente o código necessário para implementar uma interface. 

**Quando:** você deseja herdar de uma interface.  

**Por quê:** você pode implementar manualmente todas as interfaces uma por uma; no entanto, esse recurso gerará automaticamente todas as assinaturas de método. 

**Como:**

1. coloque o cursor na linha em que há um rabisco vermelho indicando que você referenciou uma interface, mas não implementou todos os membros necessários.

   ![Código realçado](media/interface-highlight-cs.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Implementar interface (explicitamente)** no pop-up da janela Visualização.
   * **Mouse**
     * Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações** e selecione **Implementar interface (explicitamente)** no pop-up da janela Visualização.
     * Passe o mouse sobre o rabisco vermelho e clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece.
     * Clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece na margem esquerda se o cursor de texto já estiver na linha com o rabisco vermelho.

   ![Visualização da implementação de classe](media/interface-preview-cs.png)

   >[!TIP]
   >Use o link [**Visualizar alterações**](../../ide/preview-changes.md) na parte inferior da janela de visualização para ver todas as alterações que serão feitas antes de fazer sua seleção.
   >
   >Além disso, você pode usar os links **Documento**, **Projeto** e **Solução** na parte inferior da janela de visualização para criar as assinaturas de método corretas em várias classes que implementam a interface.

1. As assinaturas de método da interface serão criadas automaticamente, prontas para serem implementadas.

   ![Resultado da implementação de classe](media/interface-result-cs.png)

   >[!TIP]
   >Use a opção **Implementar interface explicitamente** para iniciar cada método gerado com o nome da interface para evitar colisões de nome.
   >
   >![Implementar o resultado de interface explicitamente](media/interface-explicitresult-cs.png); 

## <a name="see-also"></a>Consulte também

[Geração de código](../code-generation-in-visual-studio.md)  
[Visualizar alterações](../../ide/preview-changes.md)  
