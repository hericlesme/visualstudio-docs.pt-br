---
title: "Remover o código inacessível - refatoração (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs: csharp
ms.openlocfilehash: d4dfc63000fe6f66135d452b9a64e14dc05101d9
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/29/2017
---
# <a name="remove-unreachable-code-in-c"></a>Remover o código inacessível em c# #
**O que:** remove o código que nunca será executado.

**Quando:** seu programa não tem nenhum caminho para um trecho de código, tornando esse trecho de código desnecessária.

**Motivo:** melhorar a legibilidade e facilidade de manutenção, removendo o código que é supérfluo e nunca será executado.

**Como:**

1. Coloque o cursor em qualquer lugar no código esmaecido limite que está inacessível:

![Código inacessível esmaecido](media/unreachablecode_faded.png)  

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione **remover código inacessível** do popup da janela de visualização.
   * **Mouse**
     * Clique com botão direito do código, selecione o **ações rápidas e refatorações** menu e selecione **remover código inacessível** do popup da janela de visualização.

1. Quando estiver satisfeito com a alteração, pressione **Enter** ou clique a correção no menu e as alterações serão confirmadas.

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
[Refatoração (C#)](../refactoring-csharp.md)  
[Visualizar alterações](../../ide/preview-changes.md)