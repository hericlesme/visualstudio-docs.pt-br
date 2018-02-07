---
title: "Remover o refatoramento do código inacessível para C# no Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: 12b6910aad6399b72b3e4bc10e6b857cc98c09bb
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2018
---
# <a name="remove-unreachable-code-in-c"></a>Remover o código inacessível no C# #

**O quê:** remove o código que nunca será executado.

**Quando:** seu programa não tem um caminho para um trecho do código, tornando esse trecho de código desnecessário.

**Por quê:** melhorar a legibilidade e a facilidade de manutenção removendo o código que é supérfluo e nunca será executado.

**Como:**

1. coloque o cursor em qualquer lugar no código esmaecido que está inacessível:

![Código inacessível esmaecido](media/unreachablecode-faded-cs.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecionar **Remover código inacessível** no pop-up da janela Visualização.
   * **Mouse**
     * Clique com o botão direito do mouse no código, selecione o menu **Ações Rápidas e Refatorações** e selecione **Remover código inacessível** no pop-up da janela Visualização.

1. Quando estiver satisfeito com a alteração, pressione **Enter** ou clique na correção no menu e as alterações serão confirmadas.

Exemplo:

```csharp
// Before
private void Method()
{
    throw new Exception(nameof(Method));
    Console.WriteLine($"Exception for method {nameof(Method)}");
}

// Remove unreachable code

// After
private void Method()
{
    throw new Exception(nameof(Method));
}
```

## <a name="see-also"></a>Consulte também

[Refatoração](../refactoring-in-visual-studio.md)  
[Visualizar alterações](../../ide/preview-changes.md)