---
title: "Mover declaração ao lado de referência - refatoração (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: d79d55ae-f6bb-4902-8db2-e7fe01bdb0bf
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: c274fd758fdae468bee884fcf1686abc16ec1d7e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="move-declaration-near-reference-in-c"></a>Mover declaração ao lado de referência em c# #
**O que:** permite mover próximo declarações de variável para seu uso.

**Quando:** ter declarações de variáveis que podem estar em um escopo mais restrito.

**Motivo:** pode deixá-lo como é, mas que podem causar problemas de legibilidade ou ocultação de informações. Esta é uma chance de refatoração para melhorar a legibilidade.

**Como:**

1. Coloque o cursor na declaração da variável.

1. Em seguida, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o **ações rápidas e refatorações** menu e selecione **mover declaração ao lado da referência** do popup da janela de visualização.
   * **Mouse**
     * Clique com botão direito do código, selecione o **ações rápidas e refatorações** menu e selecione **mover declaração ao lado da referência** do popup da janela de visualização.

1. Quando estiver satisfeito com a alteração, pressione **Enter** ou clique a correção no menu e as alterações serão confirmadas.

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
[Refatoração (C#)](../refactoring-csharp.md)  
[Visualizar alterações](../../ide/preview-changes.md)