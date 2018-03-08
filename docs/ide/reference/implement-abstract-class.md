---
title: Implementar uma classe abstrata no Visual Studio | Microsoft Docs
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
ms.openlocfilehash: 775175f5492bb8f1dd7ee2111a35ff24b273c3af
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2018
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
