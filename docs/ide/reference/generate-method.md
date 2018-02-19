---
title: "Gerar um método no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 6fbee2d6ea0a6d95d6d71114dc116cfaa1ede74e
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="generate-a-method-in-visual-studio"></a>Gerar um método no Visual Studio

Esta geração de código aplica-se a:

- C#

- Visual Basic

**O quê:** permite que você adicione imediatamente um método a uma classe.

**Quando:** você introduz um novo método e deseja declará-lo correta e automaticamente.

**Por quê:** você poderia declarar o método e os parâmetros antes de usá-los; no entanto, esse recurso gerará a declaração automaticamente.

## <a name="how-to"></a>Como fazer

1. Coloque o cursor na linha em que há um rabisco vermelho. O rabisco vermelho indica um método que ainda não existe.

   - C#:

    ![Código em C# realçado](media/method-highlight-cs.png)

   - Visual Basic:

    ![Código em VB realçado](media/method-highlight-vb.png)

1. Depois, siga um destes procedimentos:

   - **Teclado**
     - Pressione **Ctrl +.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
     - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
     - Passe o mouse sobre o rabisco vermelho e clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece.
     - Clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece na margem esquerda se o cursor de texto já estiver na linha com o rabisco vermelho.

    ![Visualização de geração do método](media/method-preview-cs.png)

1. Selecione **Gerar método** no menu suspenso.

   > [!TIP]
   > Use o link **Visualizar alterações** na parte inferior da janela de visualização [para ver todas as alterações](../../ide/preview-changes.md) que serão feitas antes de fazer sua seleção.

   O método é criado com os parâmetros inferidos com base em seu uso.

   - C#:

      ![Gerar o resultado do método C#](media/method-result-cs.png)

   - Visual Basic:

      ![Gerar o resultado do método VB](media/method-result-vb.png)

## <a name="see-also"></a>Consulte também

[Geração de código](../code-generation-in-visual-studio.md)  
[Visualizar alterações](../../ide/preview-changes.md)
