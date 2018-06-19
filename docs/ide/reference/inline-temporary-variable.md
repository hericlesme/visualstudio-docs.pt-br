---
title: Substituir uma variável temporária pelo seu valor no Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: acfbfd2a23c85c81e0956190ff8e9e8501533559
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945604"
---
# <a name="inline-a-temporary-variable-refactoring"></a>Refatoração Embutir uma variável temporária

Esta refatoração aplica-se a:

- C#

- Visual Basic

**O quê:** permite que você remova uma variável temporária e substitua-a pelo seu valor.

**Quando:** o uso da variável temporária dificulta o entendimento do código.

**Por quê:** remover uma variável temporária pode facilitar a leitura do código.

## <a name="how-to"></a>Como fazer

1. realce ou coloque o cursor do texto dentro de uma variável temporária para ser embutida:

   - C#:

    ![Código realçado – C#](media/inline-highlight-cs.png)

   - Visual Basic:

    ![Código realçado – Visual Basic](media/inline-highlight-vb.png)

1. Depois, siga um destes procedimentos:

   - **Teclado**
     - Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
     - Clique com o botão direito do mouse no código e selecione o menu **Ações e Refatorações Rápidas**.

1. Selecione **Variável temporária embutida** no pop-up da janela Visualização.

   A variável é removida e seus usos são substituídos pelo valor da variável.

   - C#:

    ![Resultado embutido – C#](media/inline-result-cs.png)

   - Visual Basic:

    ![Resultado embutido – Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)