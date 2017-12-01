---
title: "Gerar um construtor - geração de código (c#) | Microsoft Docs"
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
ms.openlocfilehash: 668036b5a9c963a48255e8425c0d443fce4b8bb7
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/29/2017
---
# <a name="generate-a-constructor-in-c"></a>Gerar um construtor em c# #
**O que:** permite gerar imediatamente o código para um novo construtor em uma classe. 

**Quando:** você introduz um novo construtor e deseja corretamente declará-la automaticamente ou modificar um construtor existente. 

**Motivo:** você pode declarar o construtor antes de usá-lo, no entanto, esse recurso irá gerar, com os parâmetros adequados, automaticamente. Além disso, modificar um construtor existente requer a atualização de todos os callsites, a menos que você use este recurso para atualizá-los automaticamente.

**Como:** para gerar um construtor de várias maneiras:
- [Gerar construtor e selecione membros](#pick)
- [Gerar Construtor de campos selecionados](#selection)
- [Gerar Construtor de uso novo](#usage)
- [Adicione o parâmetro ao construtor existente](#addparameter)
- [Criar e inicializar o campo/propriedade de um parâmetro de construtor](#create)

## <a id = "pick"></a>Gerar construtor e selecione membros
1. Coloque o cursor em qualquer linha vazia em uma classe:

   ![Cursor na linha vazia](media/constructor1_highlight.png)

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione **gerar construtor...**  do popup da janela de visualização.
   * **Mouse**
     * Clique com botão direito e selecione o **ações rápidas e refatorações** menu e selecione **gerar construtor...**  do popup da janela de visualização.
     * Clique no ![Lâmpada](media/bulb.png) ícone que aparece na margem esquerda, se o cursor de texto já está na linha vazia na classe.

   ![Gerar visualização de construtor](media/constructor1_preview.png)

1. Uma caixa de diálogo será exibida permitindo que você escolher quais membros você deseja ser usados como parâmetros de construtor, bem como solicitá-los (com cima e para baixo as setas). Pressione **Okey** para confirmar suas alterações.
  
   ![Caixa de diálogo Selecionar membros](media/constructor1_dialog.png)

   >[!TIP] 
   >Você pode verificar o **adicionar verificações nulas** caixa de seleção para gerar automaticamente verificações nulas para os parâmetros do construtor.

1. O construtor será criado com os parâmetros selecionados na ordem especificada.
   ![Gerar resultados de construtor](media/constructor1_result.png)

## <a id="selection"></a>Gerar Construtor de campos selecionados
1. Realçar os membros que você deseja ter em seu construtor gerado: ![realçar membros](media/constructor2_highlight.png)

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione **gerar construtor 'TypeName(...)'**  do popup da janela de visualização.
   * **Mouse**
     * Clique com botão direito e selecione o **ações rápidas e refatorações** menu e selecione **gerar construtor 'TypeName(...)'**  do popup da janela de visualização.
     * Clique no ![Lâmpada](media/bulb.png) ícone que aparece na margem esquerda, se o cursor de texto já está na linha com a seleção.

     ![Gerar visualização de construtor](media/constructor2_preview.png)

1. O construtor será criado com os parâmetros selecionados.
     ![Gerar resultados de construtor](media/constructor2_result.png)

## <a id="usage"></a>Gerar Construtor de uso novo
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

## <a id="selection"></a>Adicione o parâmetro ao construtor existente
1. Adicione um parâmetro para uma instanciação de objeto existente.

1. Coloque o cursor na linha em que há um rabisco vermelho, indicando que você usou um construtor que ainda não existe.
    
    ![Gerar construtor realce](media/constructor4_highlight.png)

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione **Adicionar parâmetro para 'TypeName(...)'**  do popup da janela de visualização.
   * **Mouse**
     * Clique com botão direito e selecione o **ações rápidas e refatorações** menu e selecione **Adicionar parâmetro para 'TypeName(...)'**  do popup da janela de visualização.
     * Passe o mouse sobre o Rabisco vermelho e clique no ![Lâmpada](media/bulb.png) ícone que aparece.
     * Clique no ![Lâmpada](media/bulb.png) ícone que aparece na margem esquerda, se o cursor de texto já está na linha com o Rabisco vermelho.

    ![Gerar visualização de construtor](media/constructor4_preview.png)

1. O parâmetro será adicionado automaticamente com o tipo inferido de seu uso.
   
   ![Gerar resultados de construtor](media/constructor4_result.png)

## <a id="create"></a>Criar e inicializar o campo/propriedade de um parâmetro de construtor
1. De um construtor existente, adicione um parâmetro:

   ![Gerar construtor realce](media/constructor5_highlight.png)

1. Coloque o cursor dentro do parâmetro recém-adicionado.

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione **criar e inicializar a propriedade 'YourProperty'** ou **criar e inicializar o campo 'YourField'** das Pop-up da janela de visualização.
   * **Mouse**
     * Clique com botão direito e selecione o **ações rápidas e refatorações** menu e selecione **criar e inicializar a propriedade 'YourProperty'** ou **criar e inicializar o campo 'YourField'**do popup da janela de visualização.
     * Clique no ![Lâmpada](media/bulb.png) ícone que aparece na margem esquerda, se o cursor de texto já está na linha com o parâmetro adicional.

   ![Gerar visualização de construtor](media/constructor5_preview.png)

1. A campo/propriedade será criada e automaticamente nomeada para coincidir com seus tipos.

   ![Gerar resultados de construtor](media/constructor5_result.png)
  
## <a name="see-also"></a>Consulte também  
[Geração de código (C#)](../code-generation-csharp.md)  
[Visualizar alterações](../../ide/preview-changes.md)