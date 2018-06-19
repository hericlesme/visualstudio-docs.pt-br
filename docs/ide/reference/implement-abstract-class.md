---
title: Implementar uma classe abstrata no Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e89fb94b8c68bd4ac1219b675b8e77df206bf806
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945435"
---
# <a name="implement-an-abstract-class-in-visual-studio"></a>Implementar uma classe abstrata no Visual Studio

Esta geração de código aplica-se a:

- C#

- Visual Basic

**O quê:** permite gerar imediatamente o código necessário para implementar uma classe abstrata.

**Quando:** você deseja herdar de uma classe abstrata.

**Por quê:** você pode implementar manualmente todos os membros abstratos um por um; no entanto, esse recurso gerará automaticamente todas as assinaturas de método.

## <a name="how-to"></a>Como fazer

1. coloque o cursor na linha em que há um rabisco vermelho indicando que você herdou de uma classe abstrata, mas não implementou todos os membros necessários.

   - C#:

    ![Código em C# realçado](media/abstract-highlight-cs.png)

   - Visual Basic:

    ![Código em VB realçado](media/abstract-highlight-vb.png)

1. Depois, siga um destes procedimentos:

   - **Teclado**
     - Pressione **Ctrl**+**.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
     - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
     - Passe o mouse sobre o rabisco vermelho e clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece.
     - Clique no ícone de ![Lâmpada](media/bulb-cs.png) que aparece na margem esquerda se o cursor de texto já estiver na linha com o rabisco vermelho.

   ![Visualização da implementação de classe](media/abstract-preview-cs.png)

1. Selecione **Implementar Classe Abstrata** no menu suspenso.

   > [!TIP]
   > - Use o link **Visualizar alterações** na parte inferior da janela de visualização [para ver todas as alterações](../../ide/preview-changes.md) que serão feitas antes de fazer sua seleção.
   > - Use os links **Documento**, **Projeto** e **Solução** na parte inferior da janela de visualização para criar as assinaturas de método adequadas em várias classes herdadas da classe abstrata.

   As assinaturas de método abstratas foram criadas e estão prontas para ser implementadas.

   - C#:

      ![Implementar o resultado da classe C#](media/abstract-result-cs.png)

   - Visual Basic:

      ![Implementar o resultado da classe VB](media/abstract-result-vb.png)

## <a name="see-also"></a>Consulte também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)