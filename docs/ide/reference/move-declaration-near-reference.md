---
title: Mover declaração de variável para perto da referência no Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 01/26/2018
ms.technology: vs-ide-general
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: douge
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: 7c78904123da54fd2259558f29832742d9a103d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2018
---
# <a name="move-declaration-near-reference-refactoring"></a>Mover declaração de variável para perto da referência no Visual Studio

Esta refatoração aplica-se a:

- C#

**O quê:** permite mover declarações de variável mais próximo do seu uso.

**Quando:** você tem declarações de variável que podem estar em um escopo mais restrito.

**Por quê:** você pode deixá-lo como está, mas isso pode causar problemas de legibilidade ou ocultação de informações. Esta é uma chance de refatorar para melhorar a legibilidade.

## <a name="how-to"></a>Como fazer

1. coloque o cursor na declaração da variável.

1. Depois, siga um destes procedimentos:

   - **Teclado**
     - Pressione **Ctrl**+**.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Mover declaração para próximo da referência** no pop-up da janela Visualização.
   - **Mouse**
     - Clique com o botão direito do mouse no código, selecione o menu **Ações Rápidas e Refatorações** e selecione **Mover declaração para próximo da referência** no pop-up da janela Visualização.

1. Quando estiver satisfeito com a alteração, pressione **Enter** ou clique na correção no menu e as alterações serão confirmadas.

Exemplo:

```csharp
// Before
int x;
if (condition)
{
    x = 1;
    Console.WriteLine(x);
}

// Move declaration near reference

// After
if (condition)
{
    int x = 1;
    Console.WriteLine(x);
}
```

## <a name="see-also"></a>Consulte também

- [Refatoração](../refactoring-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)