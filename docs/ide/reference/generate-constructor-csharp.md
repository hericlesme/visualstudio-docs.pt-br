---
title: "Gerar um construtor - Geração de código (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: b6e73b3b012547e98934bbcd76d1ee2eb0f3324d
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2018
---
# <a name="generate-a-constructor-in-c"></a>Gerar construtor em C# #
**O quê:** permite gerar imediatamente o código para um novo construtor em uma classe. 

**Quando:** você introduz um novo construtor e deseja declará-lo corretamente automaticamente, ou modifica um construtor existente. 

**Por quê:** você poderia declarar o construtor antes de usá-lo; no entanto, esse recurso o gerará automaticamente com os parâmetros apropriados. Além disso, modificar um construtor existente exige a atualização de todos os callsites, a menos que você use este recurso para atualizá-los automaticamente.

**Como:** há várias maneiras de gerar um construtor:
- [Gerar construtor e selecionar membros](#pick)
- [Gerar construtor desde campos selecionados](#selection)
- [Gerar construtor desde uma nova utilização](#usage)
- [Adicionar o parâmetro ao construtor existente](#addparameter)
- [Criar e inicializar o campo/propriedade de um parâmetro de construtor](#create)

## <a id = "pick"></a> Gerar construtor e selecionar membros
1. Coloque o cursor em qualquer linha vazia em uma classe:

   ![Cursor em linha vazia](media/constructor1-highlight-cs.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecione **Gerar construtor...** no pop-up da janela Visualização.
   * **Mouse**
     * Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações** e selecione **Gerar construtor...** no pop-up da janela Visualização.
     * Clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece na margem esquerda se o cursor de texto já estiver na linha vazia na classe.

   ![Visualização da geração do construtor](media/constructor1-preview-cs.png)

1. Uma caixa de diálogo será exibida permitindo que você escolha quais membros quer usar como parâmetros de construtor, bem como a ordem deles (com as setas cima e para baixo). Pressione **Ok** para confirmar suas alterações.
  
   ![Caixa de diálogo Escolher membros](media/constructor1-dialog-cs.png)

   >[!TIP] 
   >Você pode marcar a caixa de diálogo **Adicionar verificações nulas** para gerar automaticamente verificações nulas para os parâmetros do construtor.

1. O construtor será criado com os parâmetros selecionados na ordem especificada.
   ![Resultado da geração do construtor](media/constructor1-result-cs.png)

## <a id="selection"></a> Gerar construtor desde campos selecionados
1. Realce os membros que você deseja ter em seu construtor gerado: ![Realçar membros](media/constructor2-highlight-cs.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecione **Gerar construtor 'TypeName(...)'** no pop-up da janela Visualização.
   * **Mouse**
     * Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações** e selecione **Gerar construtor 'TypeName(...)'** no pop-up da janela Visualização.
     * Clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece na margem esquerda se o cursor de texto já estiver na linha com a seleção.

     ![Visualização da geração do construtor](media/constructor2-preview-cs.png)

1. O construtor será criado com os parâmetros selecionados.
     ![Resultado da geração do construtor](media/constructor2-result-cs.png)

## <a id="usage"></a> Gerar construtor desde uma nova utilização
1. coloque o cursor na linha em que há um rabisco vermelho indicando que você usou um construtor que ainda não existe.

   ![Código realçado](media/constructor-highlight-cs.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecione **Gerar construtor '*TypeName*'** no pop-up da janela Visualização.
   * **Mouse**
     * Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações** e selecione **Gerar construtor '*TypeName*'** no pop-up da janela Visualização.
     * Passe o mouse sobre o rabisco vermelho e clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece.
     * Clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece na margem esquerda se o cursor de texto já estiver na linha com o rabisco vermelho.

   ![Visualização da geração do construtor](media/constructor-preview-cs.png)

   >[!TIP]
   >Use o link [**Visualizar alterações**](../../ide/preview-changes.md) na parte inferior da janela de visualização para ver todas as alterações que serão feitas antes de fazer sua seleção.

1. O construtor será criado automaticamente com quaisquer parâmetros inferidos a partir de seu uso.

   ![Resultado da geração do construtor](media/constructor-result-cs.png)

## <a id="addparameter"></a> Adicionar o parâmetro ao construtor existente
1. Adicione um parâmetro para uma instanciação de objeto existente.

1. coloque o cursor na linha em que há um rabisco vermelho indicando que você usou um construtor que ainda não existe.
    
    ![Realce da geração do construtor](media/constructor4-highlight-cs.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecione **Adicionar parâmetro a 'TypeName(...)'** no pop-up da janela Visualização.
   * **Mouse**
     * Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações** e selecione **Adicionar parâmetro a 'TypeName(...)'** no pop-up da janela Visualização.
     * Passe o mouse sobre o rabisco vermelho e clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece.
     * Clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece na margem esquerda se o cursor de texto já estiver na linha com o rabisco vermelho.

    ![Visualização da geração do construtor](media/constructor4-preview-cs.png)

1. O parâmetro será adicionado automaticamente com o tipo inferido a partir de seu uso.
   
   ![Resultado da geração do construtor](media/constructor4-result-cs.png)

## <a id="create"></a> Criar e inicializar o campo/propriedade de um parâmetro de construtor
1. A partir de um construtor existente, adicione um parâmetro:

   ![Realce da geração do construtor](media/constructor5-highlight-cs.png)

1. Coloque o cursor dentro do parâmetro recém-adicionado.

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecione **Criar e inicializar a propriedade 'YourProperty'** ou **Criar e inicializar o campo 'YourField'** na pop-up da janela Visualização.
   * **Mouse**
     * Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações** e selecione **Criar e inicializar a propriedade 'YourProperty'** ou **Criar e inicializar o campo 'YourField'** na pop-up da janela Visualização.
     * Clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece na margem esquerda se o cursor de texto já estiver na linha com o parâmetro adicionado.

   ![Visualização da geração do construtor](media/constructor5-preview-cs.png)

1. O campo/propriedade será criado e receberá automaticamente um nome que corresponda com seus tipos.

   ![Resultado da geração do construtor](media/constructor5-result-cs.png)

## <a name="see-also"></a>Consulte também

[Geração de código](../code-generation-in-visual-studio.md)  
[Visualizar alterações](../../ide/preview-changes.md)