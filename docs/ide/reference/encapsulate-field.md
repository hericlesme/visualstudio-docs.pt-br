---
title: Refatorar um campo para uma propriedade no Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 316c1f4a6927805c75feee143f92a8e31ac4dc20
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="encapsulate-a-field-refactoring"></a>Refatoração Encapsular um campo

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O quê:** permite que você transforme um campo em uma propriedade e atualize todos os usos desse campo a fim de usar a propriedade recém-criada.

**Quando:** você quer mover um campo para uma propriedade e atualizar todas as referências a esse campo.

**Por quê:** você quer conceder a outras classes o acesso a um campo, mas não quer que essas classes tenham acesso direto.  Ao encapsular o campo em uma propriedade, você pode escrever o código para verificar o valor que está sendo atribuído, por exemplo.

## <a name="how-to"></a>Como fazer

1. realce ou coloque o cursor do texto dentro do nome do campo para encapsular:

   - C#:

    ![Código realçado – C#](media/encapsulate-highlight-cs.png)

   - Visual Basic:

    ![Código realçado – Visual Basic](media/encapsulate-highlight-vb.png)

1. Depois, siga um destes procedimentos:

   - **Teclado**
     - Pressione **Ctrl+R**, em seguida, **Ctrl+E**.  (Observe que o atalho de teclado pode ser diferente com base no perfil selecionado.)
     - Pressione **Ctrl**+**.** para disparar o menu **Ações Rápidas e Refatorações** e selecione **Encapsular campo** no pop-up da janela Visualização.
   - **Mouse**
     - Selecione **Editar > Refatorar > Encapsular Campo**.
     - Clique com o botão direito do mouse no código, selecione o menu **Ações Rápidas e Refatorações** e selecione **Encapsular campo** no pop-up da janela Visualização.

   Seleção | Descrição
   --------- | -----------
   **Encapsular campo (e usar propriedade)** | Encapsula o campo com uma propriedade e atualiza todos os usos do campo a fim de usar a propriedade gerada
   **Encapsular campo (mas ainda usá-lo)** | Encapsula o campo com uma propriedade, mas não altera qualquer uso do campo

   A propriedade é criada e as referências ao campo são atualizadas, se selecionadas.

   > [!TIP]
   > Use o link **Visualizar alterações** na janela pop-up para [ver qual será o resultado](../../ide/preview-changes.md) antes de confirmar as alterações.

   - C#:

    ![Resultado da ação de encapsular propriedade – C#](media/encapsulate-result-cs.png)

   - Visual Basic:

    ![Resultado da ação de encapsular propriedade – Visual Basic](media/encapsulate-result-vb.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)